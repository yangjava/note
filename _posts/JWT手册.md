# JWT手册

## 背景

### 跨域身份验证

Internet服务无法与用户身份验证分开。一般过程如下。

1.用户向服务器发送用户名和密码。

2.验证服务器后，相关数据（如用户角色，登录时间等）将保存在当前会话中。

3.服务器向用户返回session_id，session信息都会写入到用户的Cookie。

4.用户的每个后续请求都将通过在Cookie中取出session_id传给服务器。

5.服务器收到session_id并对比之前保存的数据，确认用户的身份。

这种模式最大的问题是，没有分布式架构，无法支持横向扩展。如果使用一个服务器，该模式完全没有问题。但是，如果它是服务器群集或面向服务的跨域体系结构的话，则需要一个统一的session数据库库来保存会话数据实现共享，这样负载均衡下的每个服务器才可以正确的验证用户身份。

例如虫虫举一个实际中常见的单点登陆的需求：站点A和站点B提供同一公司的相关服务。现在要求用户只需要登录其中一个网站，然后它就会自动登录到另一个网站。怎么做？

一种解决方案是听过持久化session数据，写入数据库或文件持久层等。收到请求后，验证服务从持久层请求数据。该解决方案的优点在于架构清晰，而缺点是架构修改比较费劲，整个服务的验证逻辑层都需要重写，工作量相对较大。而且由于依赖于持久层的数据库或者问题系统，会有单点风险，如果持久层失败，整个认证体系都会挂掉。

## 概述

JSON Web Token（JWT）是目前最流行的跨域身份验证解决方案。

官方文档是这样解释的：JSON Web Token（JWT）是一个开放标准（RFC 7519），它定义了一种紧凑且独立的方式，可以在各方之间作为JSON对象安全地传输信息。此信息可以通过数字签名进行验证和信任。JWT可以使用秘密（使用HMAC算法）或使用RSA或ECDSA的公钥/私钥对进行签名。
虽然JWT可以加密以在各方之间提供保密，但只将专注于签名令牌。签名令牌可以验证其中包含的声明的完整性，而加密令牌则隐藏其他方的声明。当使用公钥/私钥对签署令牌时，签名还证明只有持有私钥的一方是签署私钥的一方。

通俗来讲，JWT是一个含签名并携带用户相关信息的加密串，页面请求校验登录接口时，请求头中携带JWT串到后端服务，后端通过签名加密串匹配校验，保证信息未被篡改。校验通过则认为是可靠的请求，将正常返回数据。

### 什么情况下使用JWT比较适合？

授权：这是最常见的使用场景，解决单点登录问题。因为JWT使用起来轻便，开销小，服务端不用记录用户状态信息（无状态），所以使用比较广泛；
信息交换：JWT是在各个服务之间安全传输信息的好方法。因为JWT可以签名，例如，使用公钥/私钥对儿 - 可以确定请求方是合法的。此外，由于使用标头和有效负载计算签名，还可以验证内容是否未被篡改。

### 原则

JWT的原则是在服务器身份验证之后，将生成一个JSON对象并将其发送回用户，如下所示。

{

"UserName": "Chongchong",

"Role": "Admin",

"Expire": "2018-08-08 20:15:56"

}

之后，当用户与服务器通信时，客户在请求中发回JSON对象。服务器仅依赖于这个JSON对象来标识用户。为了防止用户篡改数据，服务器将在生成对象时添加签名。

服务器不保存任何会话数据，即服务器变为无状态，使其更容易扩展。

### 数据结构

改对象为一个很长的字符串，字符之间通过"."分隔符分为三个子串。注意JWT对象为一个长字串，各字串之间也没有换行符，此处为了演示需要，我们特意分行并用不同颜色表示了。每一个子串表示了一个功能块，总共有以下三个部分：

JWT的三个部分如下。JWT头、有效载荷和签名，将它们写成一行如下。

```
xxx.yyy.zzz
```

我们将在下面介绍这三个部分。

#### JWT头  **header**

JWT头部分是一个描述JWT元数据的JSON对象，通常如下所示。

{

"alg": "HS256",

"typ": "JWT"

}

在上面的代码中，alg属性表示签名使用的算法，默认为HMAC SHA256（写为HS256）；typ属性表示令牌的类型，JWT令牌统一写为JWT。

最后，使用Base64 URL算法将上述JSON对象转换为字符串保存。

#### 有效载荷	**Payload**

WT的第二部分是payload，其中包含claims。claims是关于实体（常用的是用户信息）和其他数据的声明，claims有三种类型： registered, public, and private claims。
Registered claims： 这些是一组预定义的claims，非强制性的，但是推荐使用， iss（发行人）， exp（到期时间）， sub（主题）， aud（观众）等；
Public claims: 自定义claims，注意不要和JWT注册表中属性冲突，这里可以查看JWT注册表
Private claims: 这些是自定义的claims，用于在同意使用这些claims的各方之间共享信息，它们既不是Registered claims，也不是Public claims。

有效载荷部分，是JWT的主体内容部分，也是一个JSON对象，包含需要传递的数据。 JWT指定七个默认字段供选择。

iss：发行人

exp：到期时间

sub：主题

aud：用户

nbf：在此之前不可用

iat：发布时间

jti：JWT ID用于标识该JWT

除以上默认字段外，我们还可以自定义私有字段，如下例：

{

"sub": "1234567890",

"name": "chongchong",

"admin": true

}

请注意，默认情况下JWT是未加密的，任何人都可以解读其内容，因此不要构建隐私信息字段，存放保密信息，以防止信息泄露。

JSON对象也使用Base64 URL算法转换为字符串保存。

#### 签名哈希	**Signature**

签名哈希部分是对上面两部分数据签名，通过指定的算法生成哈希，以确保数据不会被篡改。

首先，需要指定一个密码（secret）。该密码仅仅为保存在服务器中，并且不能向用户公开。然后，使用标头中指定的签名算法（默认情况下为HMAC SHA256）根据以下公式生成签名。

HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload),

secret)

在计算出签名哈希后，JWT头，有效载荷和签名哈希的三个部分组合成一个字符串，每个部分用"."分隔，就构成整个JWT对象。

### Base64URL算法

如前所述，JWT头和有效载荷序列化的算法都用到了Base64URL。该算法和常见Base64算法类似，稍有差别。

作为令牌的JWT可以放在URL中（例如api.example/?token=xxx）。 Base64中用的三个字符是"+"，"/"和"="，由于在URL中有特殊含义，因此Base64URL中对他们做了替换："="去掉，"+"用"-"替换，"/"用"_"替换，这就是Base64URL算法，很简单把。

### 工作机制

在身份验证中，当用户使用其凭据成功登录时，将返回JSON Web Token（即：JWT）。由于令牌是凭证，因此必须非常小心以防止出现安全问题。一般情况下，不应将令牌保留的时间超过要求。理论上超时时间越短越好。

每当用户想要访问受保护的路由或资源时，用户代理应该使用Bearer模式发送JWT，通常在Authorization header中。标题内容应如下所示：

Authorization: Bearer <token>
1
在某些情况下，这可以作为无状态授权机制。服务器的受保护路由将检查Authorization header中的有效JWT ，如果有效，则允许用户访问受保护资源。如果JWT包含必要的数据，则可以减少查询数据库或缓存信息。
如果在Authorization header中发送令牌，则跨域资源共享（CORS）将不会成为问题，因为它不使用cookie。

注意：使用签名令牌，虽然他们无法更改，但是令牌中包含的所有信息都会向用户或其他方公开。这意味着不应该在令牌中放置敏感信息。

### JWT的用法

客户端接收服务器返回的JWT，将其存储在Cookie或localStorage中。

此后，客户端将在与服务器交互中都会带JWT。如果将它存储在Cookie中，就可以自动发送，但是不会跨域，因此一般是将它放入HTTP请求的Header Authorization字段中。

Authorization: Bearer

当跨域时，也可以将JWT被放置于POST请求的数据主体中。

### JWT问题和趋势

1、JWT默认不加密，但可以加密。生成原始令牌后，可以使用改令牌再次对其进行加密。

2、当JWT未加密方法是，一些私密数据无法通过JWT传输。

3、JWT不仅可用于认证，还可用于信息交换。善用JWT有助于减少服务器请求数据库的次数。

4、JWT的最大缺点是服务器不保存会话状态，所以在使用期间不可能取消令牌或更改令牌的权限。也就是说，一旦JWT签发，在有效期内将会一直有效。

5、JWT本身包含认证信息，因此一旦信息泄露，任何人都可以获得令牌的所有权限。为了减少盗用，JWT的有效期不宜设置太长。对于某些重要操作，用户在使用时应该每次都进行进行身份验证。

6、为了减少盗用和窃取，JWT不建议使用HTTP协议来传输代码，而是使用加密的HTTPS协议进行传输。

## 请求流程

**1. 用户使用账号和面发出post请求；**
 **2. 服务器使用私钥创建一个jwt；**
 **3. 服务器返回这个jwt给浏览器；**
 **4. 浏览器将该jwt串在请求头中像服务器发送请求；**
 **5. 服务器验证该jwt；**
 **6. 返回响应的资源给浏览器。**

## 实现

### maven依赖

```
<dependency>
            <groupId>com.auth0</groupId>
            <artifactId>java-jwt</artifactId>
            <version>3.2.0</version>
        </dependency>
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt</artifactId>
            <version>0.7.0</version>
        </dependency>
```

### JWT工具类

用于生成Token，和Token验证

```
public class JwtUtils {
    /**
     * 签发JWT
     * @param id
     * @param subject 可以是JSON数据 尽可能少
     * @param ttlMillis
     * @return  String
     *
     */
    public static String createJWT(String id, String subject, long ttlMillis) {
        SignatureAlgorithm signatureAlgorithm = SignatureAlgorithm.HS256;
        long nowMillis = System.currentTimeMillis();
        Date now = new Date(nowMillis);
        SecretKey secretKey = generalKey();
        JwtBuilder builder = Jwts.builder()
                .setId(id)
                .setSubject(subject)   // 主题
                .setIssuer("user")     // 签发者
                .setIssuedAt(now)      // 签发时间
                .signWith(signatureAlgorithm, secretKey); // 签名算法以及密匙
        if (ttlMillis >= 0) {
            long expMillis = nowMillis + ttlMillis;
            Date expDate = new Date(expMillis);
            builder.setExpiration(expDate); // 过期时间
        }
        return builder.compact();
    }
    /**
     * 验证JWT
     * @param jwtStr
     * @return
     */
    public static CheckResult validateJWT(String jwtStr) {
        CheckResult checkResult = new CheckResult();
        Claims claims = null;
        try {
            claims = parseJWT(jwtStr);
            checkResult.setSuccess(true);
            checkResult.setClaims(claims);
        } catch (ExpiredJwtException e) {
            checkResult.setErrCode(SystemConstant.JWT_ERRCODE_EXPIRE);
            checkResult.setSuccess(false);
        } catch (SignatureException e) {
            checkResult.setErrCode(SystemConstant.JWT_ERRCODE_FAIL);
            checkResult.setSuccess(false);
        } catch (Exception e) {
            checkResult.setErrCode(SystemConstant.JWT_ERRCODE_FAIL);
            checkResult.setSuccess(false);
        }
        return checkResult;
    }
    public static SecretKey generalKey() {
        byte[] encodedKey = Base64.decode(SystemConstant.JWT_SECERT);
        SecretKey key = new SecretKeySpec(encodedKey, 0, encodedKey.length, "AES");
        return key;
    }
    
    /**
     * 
     * 解析JWT字符串
     * @param jwt
     * @return
     * @throws Exception
     */
    public static Claims parseJWT(String jwt) throws Exception {
        SecretKey secretKey = generalKey();
        return Jwts.parser()
            .setSigningKey(secretKey)
            .parseClaimsJws(jwt)
            .getBody();
    }
}
```

如何使用

```
public class LoginController {
    @Autowired
    UserRepository userRepository;
    
    @ApiOperation(value="用户登陆")
    @RequestMapping(value="login",method = RequestMethod.POST)
    public ReturnVo login(String username, String password,HttpServletResponse
            response) {
        User user =  userRepository.findByUsername(username);
        if(user!=null){
            if(user.getPassword().equals(password)){
                //把token返回给客户端-->客户端保存至cookie-->客户端每次请求附带cookie参数
                String JWT = JwtUtils.createJWT("1", username, SystemConstant.JWT_TTL);
                return ReturnVo.ok(JWT);
            }else{
                return ReturnVo.error();
            }
        }else{
            return ReturnVo.error();
        }
    }
    @ApiOperation(value="获取用户信息")
    @RequestMapping(value="description",method = RequestMethod.POST)
    public ReturnVo description(String username) {
        User user =  userRepository.findByUsername(username);
        return ReturnVo.ok(user.getDescription());
    }
}
```

## 优点

1.简洁(Compact): 可以通过`URL`，`POST`参数或者在`HTTP header`发送，因为数据量小，传输速度也很快
 2.自包含(Self-contained)：负载中包含了所有用户所需要的信息，避免了多次查询数据库
 3.因为`Token`是以`JSON`加密的形式保存在客户端的，所以`JWT`是跨语言的，原则上任何web形式都支持。
 4.不需要在服务端保存会话信息，特别适用于分布式微服务。

# SpringBoot集成JWT实现token验证

**引入`JWT`依赖,由于是基于`Java`，所以需要的是`java-jwt`**

```xml
<dependency>
      <groupId>com.auth0</groupId>
      <artifactId>java-jwt</artifactId>
      <version>3.4.0</version>
</dependency>
```

### 需要自定义两个注解

**用来跳过验证的`PassToken`**

```css
@Target({ElementType.METHOD, ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
public @interface PassToken {
    boolean required() default true;
}
```

**需要登录才能进行操作的注解`UserLoginToken`**

```css
@Target({ElementType.METHOD, ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
public @interface UserLoginToken {
    boolean required() default true;
}
```

##### `@Target`:注解的作用目标

**`@Target(ElementType.TYPE)`——接口、类、枚举、注解
 `@Target(ElementType.FIELD)`——字段、枚举的常量
 `@Target(ElementType.METHOD)`——方法
 `@Target(ElementType.PARAMETER)`——方法参数
 `@Target(ElementType.CONSTRUCTOR)` ——构造函数
 `@Target(ElementType.LOCAL_VARIABLE)`——局部变量
 `@Target(ElementType.ANNOTATION_TYPE)`——注解
 `@Target(ElementType.PACKAGE)`——包**

##### `@Retention`：注解的保留位置

**`RetentionPolicy.SOURCE`:这种类型的`Annotations`只在源代码级别保留,编译时就会被忽略,在`class`字节码文件中不包含。
 `RetentionPolicy.CLASS`:这种类型的`Annotations`编译时被保留,默认的保留策略,在`class`文件中存在,但`JVM`将会忽略,运行时无法获得。
 `RetentionPolicy.RUNTIME`:这种类型的`Annotations`将被`JVM`保留,所以他们能在运行时被`JVM`或其他使用反射机制的代码所读取和使用。**
 **`@Document`：说明该注解将被包含在`javadoc`中
 `@Inherited`：说明子类可以继承父类中的该注解**

**简单自定义一个实体类`User`,使用`lombok`简化实体类的编写**



```dart
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {
    String Id;
    String username;
    String password;
}
```

**需要写`token`的生成方法**



```tsx
public String getToken(User user) {
        String token="";
        token= JWT.create().withAudience(user.getId())
                .sign(Algorithm.HMAC256(user.getPassword()));
        return token;
    }
```

**`Algorithm.HMAC256()`:使用`HS256`生成`token`,密钥则是用户的密码，唯一密钥的话可以保存在服务端。
 `withAudience()`存入需要保存在`token`的信息，这里我把用户`ID`存入`token`中**

#### 接下来需要写一个拦截器去获取`token`并验证`token`



```java
public class AuthenticationInterceptor implements HandlerInterceptor {
    @Autowired
    UserService userService;
    @Override
    public boolean preHandle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object object) throws Exception {
        String token = httpServletRequest.getHeader("token");// 从 http 请求头中取出 token
        // 如果不是映射到方法直接通过
        if(!(object instanceof HandlerMethod)){
            return true;
        }
        HandlerMethod handlerMethod=(HandlerMethod)object;
        Method method=handlerMethod.getMethod();
        //检查是否有passtoken注释，有则跳过认证
        if (method.isAnnotationPresent(PassToken.class)) {
            PassToken passToken = method.getAnnotation(PassToken.class);
            if (passToken.required()) {
                return true;
            }
        }
        //检查有没有需要用户权限的注解
        if (method.isAnnotationPresent(UserLoginToken.class)) {
            UserLoginToken userLoginToken = method.getAnnotation(UserLoginToken.class);
            if (userLoginToken.required()) {
                // 执行认证
                if (token == null) {
                    throw new RuntimeException("无token，请重新登录");
                }
                // 获取 token 中的 user id
                String userId;
                try {
                    userId = JWT.decode(token).getAudience().get(0);
                } catch (JWTDecodeException j) {
                    throw new RuntimeException("401");
                }
                User user = userService.findUserById(userId);
                if (user == null) {
                    throw new RuntimeException("用户不存在，请重新登录");
                }
                // 验证 token
                JWTVerifier jwtVerifier = JWT.require(Algorithm.HMAC256(user.getPassword())).build();
                try {
                    jwtVerifier.verify(token);
                } catch (JWTVerificationException e) {
                    throw new RuntimeException("401");
                }
                return true;
            }
        }
        return true;
    }

    @Override
    public void postHandle(HttpServletRequest httpServletRequest, 
                                  HttpServletResponse httpServletResponse, 
                            Object o, ModelAndView modelAndView) throws Exception {

    }
    @Override
    public void afterCompletion(HttpServletRequest httpServletRequest, 
                                          HttpServletResponse httpServletResponse, 
                                          Object o, Exception e) throws Exception {
    }
```

**实现一个拦截器就需要实现`HandlerInterceptor`接口**

**`HandlerInterceptor`接口主要定义了三个方法**
 **1.`boolean preHandle ()`：
 预处理回调方法,实现处理器的预处理，第三个参数为响应的处理器,自定义`Controller`,返回值为`true`表示继续流程（如调用下一个拦截器或处理器）或者接着执行
 `postHandle()`和`afterCompletion()`；`false`表示流程中断，不会继续调用其他的拦截器或处理器，中断执行。**

**2.`void postHandle()`：
 后处理回调方法，实现处理器的后处理（`DispatcherServlet`进行视图返回渲染之前进行调用），此时我们可以通过`modelAndView`（模型和视图对象）对模型数据进行处理或对视图进行处理，`modelAndView`也可能为`null`。**

**3.`void afterCompletion()`:
 整个请求处理完毕回调方法,该方法也是需要当前对应的`Interceptor`的`preHandle()`的返回值为true时才会执行，也就是在`DispatcherServlet`渲染了对应的视图之后执行。用于进行资源清理。整个请求处理完毕回调方法。如性能监控中我们可以在此记录结束时间并输出消耗时间，还可以进行一些资源清理，类似于`try-catch-finally`中的`finally`，但仅调用处理器执行链中**

#### 主要流程:

**1.从 `http` 请求头中取出 `token`，
 2.判断是否映射到方法
 3.检查是否有`passtoken`注释，有则跳过认证
 4.检查有没有需要用户登录的注解，有则需要取出并验证
 5.认证通过则可以访问，不通过会报相关错误信息**

### 配置拦截器

**在配置类上添加了注解`@Configuration`，标明了该类是一个配置类并且会将该类作为一个`SpringBean`添加到`IOC`容器内*

```java
@Configuration
public class InterceptorConfig extends WebMvcConfigurerAdapter {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(authenticationInterceptor())
                .addPathPatterns("/**");    // 拦截所有请求，通过判断是否有 @LoginRequired 注解 决定是否需要登录
    }
    @Bean
    public AuthenticationInterceptor authenticationInterceptor() {
        return new AuthenticationInterceptor();
    }
}
```

**`WebMvcConfigurerAdapter`该抽象类其实里面没有任何的方法实现，只是空实现了接口
 `WebMvcConfigurer`内的全部方法，并没有给出任何的业务逻辑处理，这一点设计恰到好处的让我们不必去实现那些我们不用的方法，都交由`WebMvcConfigurerAdapter`抽象类空实现,如果我们需要针对具体的某一个方法做出逻辑处理,仅仅需要在
 `WebMvcConfigurerAdapter`子类中`@Override`对应方法就可以了。**

**注：
 在`SpringBoot2.0`及`Spring 5.0`中`WebMvcConfigurerAdapter`已被废弃
 网上有说改为继承`WebMvcConfigurationSupport`，不过试了下，还是过期的**

#### 解决方法:

**直接实现`WebMvcConfigurer` （官方推荐）**



```java
@Configuration
public class InterceptorConfig implements WebMvcConfigurer {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(authenticationInterceptor())
                .addPathPatterns("/**");   
    }
    @Bean
    public AuthenticationInterceptor authenticationInterceptor() {
        return new AuthenticationInterceptor();
    }
}
```

**`InterceptorRegistry`内的`addInterceptor`需要一个实现`HandlerInterceptor`接口的拦截器实例，`addPathPatterns`方法用于设置拦截器的过滤路径规则。**
 **这里我拦截所有请求，通过判断是否有`@LoginRequired`注解 决定是否需要登录**

#### 在数据访问接口中加入登录操作注解



```kotlin
@RestController
@RequestMapping("api")
public class UserApi {
    @Autowired
    UserService userService;
    @Autowired
    TokenService tokenService;
    //登录
    @PostMapping("/login")
    public Object login(@RequestBody User user){
        JSONObject jsonObject=new JSONObject();
        User userForBase=userService.findByUsername(user);
        if(userForBase==null){
            jsonObject.put("message","登录失败,用户不存在");
            return jsonObject;
        }else {
            if (!userForBase.getPassword().equals(user.getPassword())){
                jsonObject.put("message","登录失败,密码错误");
                return jsonObject;
            }else {
                String token = tokenService.getToken(userForBase);
                jsonObject.put("token", token);
                jsonObject.put("user", userForBase);
                return jsonObject;
            }
        }
    }
    @UserLoginToken
    @GetMapping("/getMessage")
    public String getMessage(){
        return "你已通过验证";
    }
}
```

**不加注解的话默认不验证，登录接口一般是不验证的。在`getMessage()`中我加上了登录注解，说明该接口必须登录获取`token`后，在请求头中加上`token`并通过验证才可以访问**

