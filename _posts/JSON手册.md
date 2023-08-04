[TOC]

# JSON 手册

## JSON简介

JSON(JavaScript Object Notation)是一种轻量级的数据交换格式，它基于JavaScript的一个子集，易于人的编写和阅读，也易于机器解析。

JSON采用完全独立于语言的文本格式，但是也使用了类似于C语言家族的习惯（包括C, C++, C#, Java, JavaScript, Perl, Python等）。 这些特性使JSON成为理想的数据交换语言。

## JSON 实例

```javascript
{
  "users": [
  { "name":"杨京京",age:18},
  { "name":"张三" , age:15},
  { "name":"李四" , age:16}
  ]
}
```

这个 users对象是包含 3 个用户对象（对象）的数组。

## JSON结构

JSON由两种结构组成：

1. 键值对的无序集合——对象(或者叫记录、结构、字典、哈希表、有键列表或关联数组等)
2. 值的有序列表——数组

这些都是常见的数据结构。事实上大部分现代计算机语言都以某种形式支持它们。这使得一种数据格式在同样基于这些结构的编程语言之间交换成为可能。

## JSON形式：

### JSON对象object

对象是一个无序键值对的集合，以"**{**"开始，同时以"**}**"结束，键值对之间以"**:**"相隔，不同的键值对之间以"**,**"相隔。



![img](https:////upload-images.jianshu.io/upload_images/5656674-a46d19f70eb18009.png?imageMogr2/auto-orient/strip|imageView2/2/w/598/format/webp)

举例

```javascript
{
    "name" : "杨京京",
    "age" : 18
}
```

### JSON数组array

数组是值（value）的有序集合。一个数组以“[”（左中括号）开始，“]”（右中括号）结束。值之间使用“,”（逗号）分隔。



![img](https:////upload-images.jianshu.io/upload_images/5656674-e28f2f7e6a8fc86b.png?imageMogr2/auto-orient/strip|imageView2/2/w/598/format/webp)

举例

```javascript
[ "Google", "baidu", "Taobao" ]
```

或者

JSON对象中的数组

```javascript
{
"name":"用户",
"num":3,
"sites":[ "杨京京", "张三", "李四" ]
}
```

### JSON值value

值（value）可以是双引号括起来的字符串（string）、数值(number)、true、false、 null、对象（object）或者数组（array）。这些结构可以嵌套。

![img](https:////upload-images.jianshu.io/upload_images/5656674-9332d7c9d600ef19.png?imageMogr2/auto-orient/strip|imageView2/2/w/598/format/webp)



JSON 值可以是：

- 字符串（在双引号中）
- 数字（整数或浮点数）
- 逻辑值（true 或 false）
- 数组（在中括号中）
- 对象（在大括号中）
- null

### JSON字符串string

字符串（string）是由双引号包围的任意数量Unicode字符的集合，使用反斜线转义。一个字符（character）即一个单独的字符串（character string）。

字符串（string）与C或者Java的字符串非常相似。

![img](https:////upload-images.jianshu.io/upload_images/5656674-828c1c1295e1581d.png?imageMogr2/auto-orient/strip|imageView2/2/w/598/format/webp)

举例

```javascript
{
    "name" : "杨京京"
}
```



### JSON数值number

数值（number）也与C或者Java的数值非常相似。除去未曾使用的八进制与十六进制格式。除去一些编码细节。

![img](https:////upload-images.jianshu.io/upload_images/5656674-2c76ef32ef87e0c8.png?imageMogr2/auto-orient/strip|imageView2/2/w/598/format/webp)

```javascript
{
    "age" : 18
}
```

### JSON 布尔值

JSON 布尔值可以是 true 或者 false：

举例

```javascript
{ 
     "flag":true 
}
```

### JSON null

JSON 可以设置 null 值：

```javascript
{ "name":null }
```

空白可以加入到任何符号之间。

### JSON 文件

- JSON 文件的文件类型是 ".json"
- JSON 文本的 MIME 类型是 "application/json"



具体参见JSON官网http://www.json.org/json-zh.html

很多语言都提供了JSON的解析库。

##  JavaScript  

### 访问JSON对象

 你可以使用点号（.）来访问对象的值： 

```javascript
var jsonObj, x;
jsonObj = { "name":"杨京京", age:18};
x = myObj.name;
```

或者 你也可以使用中括号（[]）来访问对象的值： 

```javascript
var jsonObj, x;
jsonObj = { "name":"杨京京", age:18};
x = myObj["name"];
```

## 循环对象

你可以使用 for-in 来循环对象的属性：

```javascript
var myObj = { "name":"杨京京", age:18};
for (x in myObj) {
   console.log("log"+x);
}
```

 在 for-in 循环对象的属性时，使用中括号（[]）来访问属性的值： 

```javascript
var myObj = { "name":"杨京京", age:18};
for (x in myObj) {
    console.log("log"+myObj[x]);
}
```

## 嵌套 JSON 对象

JSON 对象中可以包含另外一个 JSON 对象：

```javascript
myObj = {
    "name":"runoob",
    "alexa":10000,
    "sites": {
        "site1":"www.runoob.com",
        "site2":"m.runoob.com",
        "site3":"c.runoob.com"
    }
}
```

 你可以使用点号(.)或者中括号([])来访问嵌套的 JSON 对象。 

```javascript
x = myObj.sites.site1;
// 或者
x = myObj.sites["site1"];
```

### 修改值

你可以使用点号(.)来修改 JSON 对象的值：

```javascript
myObj.sites.site1 = "www.google.com";
```

 你可以使用中括号([])来修改 JSON 对象的值： 

```javascript
myObj.sites["site1"] = "www.google.com";
```

## 删除对象属性

我们可以使用 **delete** 关键字来删除 JSON 对象的属性：

```javascript
delete myObj.sites.site1;
```

 你可以使用中括号([])来删除 JSON 对象的属性： 

```javascript
delete myObj.sites["site1"]
```

##  FastJson 

### **FastJson**简介

 FastJson是用于java后台处理json格式数据的一个工具包，包括“序列化”和“反序列化”两部分，它具备如下特征： 

- 速度最快，测试表明，fastjson具有极快的性能，超越任其他的java json parser。
- 功能强大，完全支持java bean、集合、Map、日期、Enum，支持范型，支持自省。
- 无依赖，能够直接运行在Java SE 5.0以上版本 

### **FastJson**依赖

```
<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>fastjson</artifactId>
	<version>1.2.47</version>
</dependency>
```

###  **FastJson** 常用方法

 FastJson对于json格式字符串的解析主要用到了一下三个类： 

- JSON：fastJson的解析器，用于JSON格式字符串与JSON对象及javaBean之间的转换。
- JSONObject：fastJson提供的json对象。
- JSONArray：fastJson提供json数组对象

### FastJson实例

实例运行需要的Java对象

```java
@Data
public class LoginAccount implements Serializable {

    private Long id;

    private String loginName;

    private String type;

    private Date LoginTime;

}
```

```java
@Data
public class User implements Serializable {

    private Long id;

    private String name;

    private Integer age;

    private Date birthDay;

    private Boolean isMale;

    private Double balance;

    private List<LoginAccount> loginAccountList;
}
```

#### Java对象转为Json字符串

```java
        User user=new User();
        user.setId(1L);
        user.setName("杨京京");
        user.setAge(18);
        user.setIsMale(true);
        user.setBirthDay(new Date());
        user.setBalance(100000.00);
        LoginAccount loginAccount1=new LoginAccount();
        loginAccount1.setId(1L);
        loginAccount1.setLoginName("用户名登录");
        loginAccount1.setType("name");
        loginAccount1.setLoginTime(new Date());

        LoginAccount loginAccount2=new LoginAccount();
        loginAccount2.setId(2L);
        loginAccount2.setLoginName("邮箱登录");
        loginAccount2.setType("email");
        loginAccount2.setLoginTime(new Date());
        List<LoginAccount> loginAccounts=new ArrayList<>();
        loginAccounts.add(loginAccount1);
        loginAccounts.add(loginAccount2);
        user.setLoginAccountList(loginAccounts);
        String s= JSON.toJSONString(user);
        System.out.println("objectToJsonString========="+s);
```

输出结果

```java
objectToJsonString========={"age":18,"balance":100000.0,"birthDay":1574742685474,"id":1,"isMale":true,"loginAccountList":[{"id":1,"loginName":"用户名登录","loginTime":1574742685474,"type":"name"},{"id":2,"loginName":"邮箱登录","loginTime":1574742685474,"type":"email"}],"name":"杨京京"}
```



#### 总结

（1）对于JSON对象与JSON格式字符串的转换可以直接用 toJSONString()这个方法。
（2）javaBean与JSON格式字符串之间的转换要用到：JSON.toJSONString(obj);
（3）javaBean与json对象间的转换使用：JSON.toJSON(obj)，然后使用强制类型转换，JSONObject或者JSONArray。
