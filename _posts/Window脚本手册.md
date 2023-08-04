# Window脚本手册

# 第一章：前言

无意中发现了批处理的强悍作用是不容忽视的，而在几周之前我连其概念都不知道。批处理在某些情况下有着与编程类似的思想，有人说批处理是一种宏。从应用范围上来看，批处理的用途非常广泛。了解到了其实用性，加之我有C语言做基础，是以有了学习批处理的想法。可以说我对批处理的学习几乎是从零开始的，只是在工作之余在网上自行搜索浏览探索尝试的。如果您也对批处理有兴趣的话，不妨看看下文，共同学习一番。

[声明]：本文可以作为了解并熟悉批处理的参考，但并不保证文中所有的概念、理论、用法及操作的正确性或规范性。如果本文(系列)存在错误或纰漏，本人对此表示抱歉，并欢迎读者指正。

1.1 什么是批处理？

从内容上看，批处理文件包含了大量的基本DOS命令，是一种可执行文件。该文件运行时能按照其规则将其中的命令逐一执行。使用批处理文件进行的批量的命令处理的过程，称之为批处理。
批处理文件(Batch File，简称BAT文件)是一种在DOS下最常用的可执行文件。它具有灵活的操纵性，可适应各种复杂的计算机操作。所谓的批处理，就是按规定的顺序自动执行若干个指定的DOS命令或程序。即是把原来一个一个执行的命令汇总起来，成批的执行，而程序文件可以移植到其它电脑中运行，因此可以大大节省命令反复输入的繁琐。同时批处理文件还有一些编程的特点，可以通过扩展参数来灵活的控制程序的执行，所以在日常工作中非常实用。[1]

批处理文件的后缀名为.bat(Batch的缩写)。可以用绝大多数的文本编辑工具进行编辑。由于批处理文件的实质就是一个命令的集合，所以批处理文件的工作平台是由这些命令所工作的平台来决定，如今Microsoft环境下的批处理文件(.bat和.cmd文件)的平台，当然也就是Microsoft的DOS和Windows系统。[1]

1.2 了解与使用基本DOS命令

说到批处理，我们不得不先讨论一些基本的DOS命令。对于“命令”("Command")一词，实际上就体现了我们与计算机的交流过程。比如，您可以通过使用鼠标点击“开始”，选择关机来命令计算机执行关闭计算机的行动；您也可以通过只是简单地双击一下桌面上的《星际争霸》快捷方式来让计算机运行《星际争霸》这款经典的即时战略游戏。也许您认为这些命令就如同吃饭睡觉一样简单，这是因为图形化界面已经为我们把复杂难以理解的命令操作封装成人人都能非常容易上手的操作方式，使得我们只需要点点鼠标或是敲几下键盘就能轻而易举地完成。

而DOS命令，对于不少新接触计算机的朋友来说可能是一个高深而神秘的词。不过，如果您多少还懂点英语的话，这些问题可能就变得是很容易被理解的。假如我们打算把电脑D盘里的一个叫做"a.txt"的文本文件复制到E盘里，您也许能够提出使用Ctrl+C复制该文件，然后再在E盘中Ctrl+V将其粘贴到此处；或是建议按住Ctrl键然后直接拖动到E盘，又或是用右键拖动后再选择，等等。这些都是图形界面里的操作，如果我们想用DOS命令来实现这一操作该如何去做呢？copy D:\a.txt E:\a.txt 这句英文看起来更像是在尝试与电脑进行聊天。不过您必须得保证您的发言有着严格正确的格式，电脑才会按照您的意图去执行。以下为常用文件操作DOS命令：

dir 　　　列文件名
cd　　　　改变当前目录
ren 　　　改变文件名
copy　　　拷贝文件
del 　　　删除文件
md　　　　建立子目录
rd　　　　删除目录
deltree　 删除目录树
format　　格式化磁盘
edit　　　文本编辑
type　　　显示文件内容
mem 　　　查看内存状况
以下是新增加的命令
help　　　显示帮助提示
cls 　　　清屏
move　　　移动文件，改目录名
more　　　分屏显示
xcopy 　　拷贝目录和文件
[2]

仅仅是告诉您有哪些命令可以使用，此时您仍不会明白DOS命令的操作用法。我们不妨从例子中学习并理解。

可以在 开始->所有程序->附件->命令提示符 找到并打开MS-DOS命令提示符。或是按WIN键(键盘上有微软标示的那个按键)再按R键，然后输入 cmd 并按回车，也能打开命令提示符。无论您对这个黑色而单调的界面感到是多么的新奇、或是陌生、甚至是厌恶，此时您都不会再计较了，重要的是您得尝试一下所谓的DOS命令。如果您正在用Windows XP操作系统(XP自带的DOS5使用方便，便于理解，以下均以XP操作系统为例进行说明)，您将可能看到有类似 C:\Documents and Settings\Administrator> 的这么一行文字。这说明，您此时的工作位置就在 C:\Documents and Settings\Administrator 里。当然 Administrator 也可能是别的词，这取决于您当前登录的用户名以及该用户所设定文件夹的名称。而使用 Windows9X 操作系统的命令提示符将会看到经典的 C:\WIDNOWS> 。

此时我们来尝试一下使用一些基本的DOS命令，
比如，键入 dir (不区分大小写)并按回车后，我们会得到当前文件夹下所有的子文件夹和文件的相关信息。输入 dir c:\windows ，可以查看指定的路径文件夹(这里假定我们指定的文件夹是C盘的WINDOWS文件夹)中的信息。在输入该命令后，只见刷地一下啥也没看清，N多文件或文件夹就已一闪而过，因为一个屏幕无法显示这么多的文件或文件夹。好在在DOS5中我们可以用鼠标滚轮向前滚动查看更多的内容。然而，早期的DOS版本并不具有保存多页信息的功能，我们不妨使用 dir 的一些参数(适当的参数加在相应的命令后面可以实现更多的扩展功能)，比如 /p ，即输入 dir c:\windows /p 。这样就能在每显示一个屏幕的内容后暂停一下以便查看。

关于 dir 命令的用法和参数还有更多。除了 dir 以外，每一种命令的用法和参数都不少。看到这里您也许会觉得很沮丧，认为自己没有天赋、也没有工夫来死记硬背这些该死的命令。事实上我也有同感。命令的具体用法在帮助里、在网上都能轻而易举地找到。只要输入 dir /? 就能得到关于dir命令完整的使用介绍，而且是中文的。同理，任何命令后面跟上 /? 的参数，都能得到该命令的完整说明。当然，也可以在网上搜索"DOS命令"等关键字来查找具体的DOS用法(推荐一个洪恩在线)。我们所需要的只是知道执行什么操作时用什么命令就行了，即使是连命令的名称都记不得了也没关系，都是现学现用的嘛。

很多情况下，我们只需要记住一条命令 help ，就能掌握整个DOS命令。比如直接输入 help 可以得到命令的帮助信息。输入 help dir 就能得到命令 dir 的具体参数及其用法(等同与 dir /? )。不仅仅是DOS命令，很多带有命令提示的工具都有help提供帮助和提示，例如MATLAD中的命令行，又如BattleNet中的以斜杠 / 开头的命令等等。

下面以一段例子来介绍DOS命令的具体用法(灰色背景的文字为DOS命令，可以尝试在命令提示符中输入测试查看效果)。

d:
转到驱动器D盘下，此时我们能看到 D:\> 的提示符(前提是您的电脑硬盘必须至少划分出D盘)。如果看到的不是就再输入下一行命令。
cd\
这一条命令 cd 的作用是改变当前的工作目录，后面加上 \ 表示返回到该驱动器的最顶级目录。另外，一个句点 . 表示当前文件夹，两个连续的句点 .. 则表示上一级文件夹， cd.. 即目录向上一级。
md test
正如前文所说，命令 md 的作用是创建子目录，此时打开D盘看一看，是不是多了一个名叫test的文件夹(如果不是事先早已存在的话)。事实上该命令的完整写法为 md d:\test ，由于当前目录已经在D盘了，所以我们把具体的路径给简化了。
md "test my folder"
同理，在D盘创建一个名为test my folder的文件夹。加双引号的目的是告诉计算机我们要创建一个名字中含有空格的文件夹，而不是分别创建名字分别为test、my和folder的3个不同的文件夹。注：除了空格以外，在路径或文件名中含有 &()[]{}^=;!'+,`~ 特殊字符时也需要用双引号引用起来，以便机器能够正确地识别。
cd test
改变当前工作目录，此时不再是D盘了，而是在 D:\test 的目录下。
echo Hello world>a.txt
遇到了一个新命令 echo ，它可以将某某内容显示出来。只考虑 echo Hello world 就是把字符串 Hello world 显示出来而已。后面使用了符号 > 表示将这句 Hello world 写入到某文件中。结果为：在 D:\test 文件夹里多了一个叫 a.txt 的文件，其内容为 Hello world 。
copy a.txt "d:\test my folder"
这就是将当前文件夹里的那个 a.txt 文件复制到 D:\test my folder 文件夹中
copy a.txt "..\test my folder\b.txt"
还是复制 a.txt ，但这次的路径与上一条命令的写法不同。 .. 表示先向上一级，再挪到 test my folder 文件夹里。其实还是复制到 D:\test my folder 这个文件夹里了。这次复制过去的文件名也不一样，因为这次我们指定了要复制过去的目标文件名为 b.txt 。
copy a.txt "..\test my folder\c.bmp"
再次复制 a.txt 到同样的文件夹里。不过这次不光改文件的标题名了，连文件的后缀名也改了。打开 D:\test my folder 文件夹检查一下，是不是多了名字分别叫 a.txt b.txt c.bmp 的3个文件。
cd..
向上一级
cd "test my folder"
进入 D:\test my folder 文件夹
ren c.bmp d.bin
重新命名文件 c.bmp 为 d.bin 。完整地写法为 ren "d:\test my folder\c.bmp" d.bin 。
del *.txt
删除当前工作目录中所有文件后缀名为 .txt 的文件。 * 表示通配符。例如：a.* 表示所有文件标题为 a 的文件，不论后缀名。 *.* 则表示任何标题名和任何后缀名的文件，即所有文件。此时结果应为：该目录里的 a.txt b.txt 这两个文件已经不存在了，即使是在回收站里也找不到了。
cd..
向上一级
rd test "test my folder"
这一条命令是想同时移除 test 和 test my folder 这两个文件夹。不过结果并没有成功，因为它会提示：目录不是空的。test 文件夹中有 a.txt ，test my folder 文件夹中还有 d.bin ，因此文件夹删不掉。
rd test "test my folder" /s
如果加上 /s 这个参数后就能删除这两个文件夹以及其文件夹中所包含的所有内容了。注意：删除前请确认这些文件夹是否是您以前就有的文件夹，或者说里面是否存有任何有用文件，不要因为这个测试而丢掉了重要文件。

1.3 我们的第一个批处理

在阅读本文之前您可能还对此一无所知，而现在您却已经略知一二了。如果您还无法理解DOS命令的工作原理或方式，在继续阅读下文之前，强烈建议具体操作实践一下。

不过说了那么多，看起来似乎还没进入正题，您可能会不耐烦地说：目前批处理连个影子都没见到呢。如果我们只是简单地将上述例子中的命令集合起来，那么这就形成了一个批处理。做法是：先打开记事本，把下面这些您已经了如指掌(或者说只是略知一二)的命令复制进去。然后保存到某处(比如桌面)，并命名为 MyFirstBatch.bat (文件标题可自拟，但后缀名必须是.bat)。

::::::::::::::::::::::::::::::::
md "d:\test" "d:\test my folder"
echo Hello world>"d:\test\a.txt"
copy "d:\test\a.txt" "d:\test my folder"
copy "d:\test\a.txt" "d:\test my folder\b.txt"
copy "d:\test\a.txt" "d:\test my folder\c.bmp"
ren "d:\test my folder\c.bmp" d.bin
::::::::::::::::::::::::::::::::

看到了吧！惊喜吧！疯狂吧！一个自己写的，或者说至少是自己已经能够完全理解的批处理文件 MyFirstBatch.bat 就这样诞生了。或许此时您对这东西能否正常工作还持有怀疑态度，但是在看到对该批处理文件双击运行完的结果以后，先前或多或少的怀疑也就荡然无存了……

双击后，显示的只是一闪就关闭了。正确的结果是在D盘多了名字分别为 test 和 test my folder 的两个文件夹。文件夹 test 里有一个叫 a.txt 的文件。而文件夹 test my folder 里有名字分别为 a.txt b.txt 和 d.bin 的3个文件。

# 第二章：显示篇

有了前文作铺垫和基础，后面的便容易理解多了。这里主要讨论的是批处理过程中与显示相关的命令用法。先看一下 echo、@、pause、>、>>、title 、rem 这几个命令或符号的用法。

2.1 echo @ 和 pause

在DOS命令提示符中使用 echo /? 可以获得对 echo 用法的解释。echo on 用于打开命令的回显；echo off 用于关闭命令的回显(默认情况下，ehco 是处于打开状态的)。只输入 echo 可以获得当前的回显状态(是否处于打开状态)。输入 echo 再加一段文字，例如 echo Hello world! 可以显示出 Hello world! 这句信息。

@ ，如果在某一条命令最前面加上 @ ，那么这一行命令就不会显示出来。与 echo off 有着相似之处。 echo off 以后的所有命令本身都不再显示出来；而 @ 只是将当前那一行的命令不显示出来。然而，至于命令所产生的输出结果，仍然会显示出来。这看起来似乎有些拗口，但我们会通过例子来很容易地理解它们。

pause ，从字面上看就是暂停的意思，效果等同于将程序挂起，在按下任意键后才继续。

::::::::测试显示状态.bat::::::::
echo
pause

echo 例句一 此时回显为打开状态，因此前一句显示了命令行
@echo 例句二 此时回显虽然为打开状态，但命令前使用了@，因此未显示命令行本身
pause

echo off
echo
echo 例句三 此时回显为关闭状态，因此未显示命令行本身
@echo 例句四 此时回显为关闭状态且使用了@，因此未显示命令行本身
pause
::::::::::::::::::::::::::::::::

上面的这一段批处理测试，有效地展示了在使用 echo on 和 echo off ，以及在命令前加上 @ 符号后，命令行本身的显示效果。

2.2 > 和 >>

\> 表示将输出结果打印到某处。比如：echo Hello world!>d:\a.txt 表示将 Hello world! 这句话写入到 D:\a.txt 文件中。如果以前该文件中已经存在，并且有自己的内容，那么以前的内容就被覆盖掉了。比如我们再输入：echo yo, whats up>d:\a.txt ，那么文件 a.txt 中以前的 Hello world! 就变成了现在的新例句。

\>> 与 > 类似，也可以将输出结果打印到某处。比如我们用 echo nothin much, and u?>>d:\a.txt 将例句写到 a.txt 里时，该例句并不会覆盖原有的 yo, whats up 这句话，而是加在了原句的后面。

如果一条命令后面跟上 >nul ，比如 pause>nul 表示将 pause 这条命令的输出显示到空设备里， nul 表示为空。用了 pause>nul 这条命令后，"按任意键继续..."的提示就不再出现了。

对比 echo off、@ 和 >nul 。echo off 表示这以后的所有命令的本身不再显示了，直到后面有 echo on 的出现。而加在命令行前面的 @ 只是让当前这一行命令不显示。加在命令行后面的 >nul 却可以让该命令的输出不显示。

2.3 title 和 rem

title 后面跟字符串可以改变当前命令提示符的标题名称。输入 title 这是新标题 后，该命令提示符左上角的标题名称已经变为"这是新标题"了。输入中文可以通过 Ctrl+空格 切换出中文输入法；也可以通过复制粘贴的方式输入。

rem 的用法就很简单了，rem 后面跟上一段文字，在批处理中可以作为注释用。rem 和它后面跟的文字在实际运行时并不会起任何作用，只是为了方便人们阅读该批处理时更容易理解而已(如果您用过C的话，一定会联想到C语言里的 // 或 /* */ 的用法)。除了 rem 外，两个连续的冒号 :: 也起同样的作用。提示：rem 与 :: 的区别在于，rem 也是一种命令，在 echo on 的情况下会被显示出来，而 :: 却不会。

:::::::测试标题和注释.bat:::::::
@echo off
rem 上条命令表示以后所有的命令行不再显示自身，@表示连echo off这一句都不显示，当前这一行只是注释而已，不参与程序的运行。

echo 欢迎！
pause

title 现在标题已经换成这句了
echo 标题已更改

echo 现在使用了暂停，按任意键后该批处理结束~
pause>nul
rem 不显示pause的输出提示，而是使用我们自己定义的暂停提示。
::::::::::::::::::::::::::::::::

2.4 其他命令

prompt ，这就是命令提示符中所谓的"提示符"了。在命令提示符中输入 prompt 加一段文字能够使得提示符不再是以传统的路径名和大于号组成的，而是以我们刚才输入的那段文字开头的。这也许不是很好理解，或者您对 prompt 的含义还不清楚或只知道其字面含义。这并不要紧，如果您只要简单地输入 prompt 提示符 就能很快地明白 prompt 的含义了。此外，要想恢复以前的路径名和大于号为开头的提示符，只需要再输入 prompt $p$g 即可。这里$p 表示当前驱动器和路径， $g 表示大于号。因为一些特殊的格式或符号需要用 $ 加特定的字母来表示。具体的说明可以用 help prompt 来查询。

# 第三章：赋值 调用 参数

3.1 赋值

3.1.1 给变量赋予一个文字字符串的值

说到赋值，就得先弄懂 set 这条命令。set 这条命令比较复杂，在命令提示符中键入 set /? 后得到的帮助信息也很多。不过，简单地说，使用 set 跟上变量，再用等号 = 跟上字符串就能简单地给该变量赋值了。例如 set var=Hello world! 。为了确认一下变量 var 的值是否是 Hello world! ，可以用 set var 来查看变量 var 的值。用 set v 可以查看所有以字母 v 开头变量的值。直接输入 set 可以查看所有变量的值。另外，变量两侧加上百分符号 % 用来表示该变量的值(内容)。这样做可以将该变量的值赋给其他变量或是用做计算显示等处理。

3.1.2 给变量赋予一个数值型的值

在 set 后面加上 /a 的参数可以给变量赋予一个数值型的值，例如 set /a var=48 表示将数字48赋给变量var。该数值型的变量是一个32位的整数型数值，即占用4个字节，能表示的数值个数为2的32次方，含正负号，范围为：-2147483648~2147483647。

3.1.3 从外部获得输入的赋值方式

在 set 后面加上 /p 的参数，可以将变量设成用户输入的一行输入。读取输入行之前，显示指定的 提示文字。当然，提示文字也可以是空的。比如 set /p var=请输入一些文字： ，可以显示出一段提示文字"请输入一些文字："并能将用户输入的信息存到变量var里。/p 的参数还有很多诸如对字符串的替代、提取、增减等功能，具体可以参考 set 的相关帮助信息。

3.1.4 变量的值的赋予、显示、变换、计算等功能

可能此时有些朋友对百分号 % 的理解还处于迷茫状态，对此我们可以做一些实验。首先，就像前文所说的那样，给一个叫做 var 的变量赋值Hello world! (在命令行里输入 set var=Hello world! )。然后我们的打算把变量 var 里的值赋给另一个变量 var1 ，做法是：set var1=%var% ，此时 var1 里的值也是 Hello world! 了。假如不使用百分号 % 仅仅是 set var1=var 的话，那么此时变量 var1 所得到的值仅仅是 var 这3个字母而已。再回顾一下 echo 的用法，分别尝试输入 echo var1 和 echo %var1% ，所得到的返回输出分别为：var1 和 Hello world! 。

此外，百分号可以对变量中的字符串有效地进行编辑或变换。
值得一提的是替换功能，其格式为：原始变量的名称后面跟上冒号 : ，再加上想要被代替的内容，紧接着一个等号 = ，然后再加上用来代替的新内容，最后用两个百分号把以上这些包括起来即可。虽然此时原始变量的值并没有改变，但百分号里的内容可以赋给一个变量，这个变量可以是原始变量。例：echo %var:o=z% ，效果为把 Hello world! 里所有的字母 o 都用字母 z 代替，并显示出来，然而变量 var 的值却没有变化。
当然，我们并不会满足于仅仅是代替一个字母——有时候我们需要代替两个。set var2=%var:ld=ms and bugs% ，这条命令可以在把 Hello world! 里的 ld 替换成 ms and bugs 并将新的结果赋给变量 var2 ，变量 var 仍然不会变化。输入 echo %var2% 确认一下结果是否为我们所期待的 Hello worms and bugs! 。

对变量中的字符串在特定位置上的删减将用到这样的格式：%var:~m% 和 %var:~m,n% 。m 和 n 为整数参数。数字 m 为正数表示取变量 var 中从左侧数第 m 个字符(单字节字符)以后的内容；m 为负数则表示取变量 var 从右侧数第 -m 个字符以及其右侧的所有的字符，这就是第一条命令所产生的新字符串。如果数字 n 为正数，表示在上述新字符串中，从其左侧取 n 个字符的内容；若 n 为负数，则从其左侧取字符直到还剩下 -n 个字符为止的内容。

如果您坚持认为这种抽象的表达方式是根本无法解释清楚这该死的 m 和无耻的 n 究竟是怎么回事的话，不如实验一下下面的例子。为了方便查看效果，我们假定变量 var 中的内容为 1234567890 (set var=1234567890)，然后依次输入以下命令并查看相应的结果。
输入的命令　　　　结果　　　　效果　　　　　　　　　　　　　　　　　　　
echo %var%　　　　1234567890　显示所有　　　　　　　　　　　　　　　　　
echo %var:~4%　　 567890　　　从第4个字符以后开始显示　　　　　　　　　
echo %var:~4,3%　 567　　　　 从第4个字符以后开始显示，并只显示前3个　　
echo %var:~-4%　　7890　　　　从倒数第4个字符开始显示　　　　　　　　　
echo %var:~-4,3%　789　　　　 从倒数第4个字符开始显示，并只显示前3个　　
echo %var:~4,-2%　5678　　　　从第4个字符以后开始显示，显示到还剩2个为止
echo %var:~0,3%　 123　　　　 从头开始显示，并只显示前3个字符　　　　　
echo %var:~0,-3%　1234567　　 从头开始显示，显示到还剩3个字符为止　　　

此外，set 也可以对数值型的变量进行常见的运算操作。
set /a num=48
set /a result=%num%+12
echo %result%
上面的命令表示先给数值 48 赋给变量 num ，然后再把变量 num 的数值与数值 12 相加后的结果赋给变量 result 。第3行可以显示变量 result 的值，结果很明显，是 60 。

3.2 调用

与很多编程类的东西一样，批处理并不一定非得按照文本中命令的排列顺序一行一行地执行。如果遇到了 goto、call、start 这样的跳转、调用、启动等语句，程序通常会变得多层化，执行起来会更加有效。

3.2.1 跳转

goto 对于多少有点编程基础的朋友来说，想必不是一件难以理解的东西。goto 跟上标签就能直接让程序从该标签处开始继续执行随后的命令，不论标签的位置是在该 goto 命令的前面还是后面。标签必须以单个冒号 : 开头，但不区分大小写。有个特殊的标签 :EOF 或 :eof 能将控制转移到当前批脚本文件的结尾处，它是不需要事先定义的。
::::::::::::跳转.bat::::::::::::
@echo off
goto :FirstLable

:SecondLable
echo 然后显示这句
pause
goto :EOF

:FirstLable
echo 首先显示这句
pause
goto :SecondLable
::::::::::::::::::::::::::::::::

3.2.2 调用

call 主要体现在两个方面：一是调用该批处理以外的另一个批处理(事实上调用该批处理本身也可以，只是可能会带来不必要的死循环)；另一方面是有着与 goto 类似的向特定标签处跳转的功能。然而，call 的独特之处在于：在调用的批处理或标签后的内容处理完成以后，控制会继续执行 call 后面的语句。我们先来看一下用 call 进行跳转的效果。为了方便对比，我们将上面的批处理作如下修改(浅色文字为修改部分)。
::::::::::::跳转.bat::::::::::::
@echo off
call :FirstLable

:SecondLable
echo 然后显示这句
pause
goto :EOF

:FirstLable
echo 首先显示这句
pause
::goto :SecondLable
::::::::::::::::::::::::::::::::
在用 call 跳转到 :FirstLabel 处执行到程序结尾后(此时 call 的任务才刚刚完成)，会继续回到 call 语句后的 :SecondLabel 处。假如 goto :SecondLabel 这一句没有被注释掉的话，那么控制会跳转到 :SecondLabel 处直到 goto :EOF 处 call 的使命才真正完成。而且，call 在完成任务后，下面的 :SecondLabel 处内容会再次执行一遍。

当 call 作为调用其他新的批处理的用途时，当前批处理就会暂停，直到新的批处理结束后，之前的批处理才会继续执行。例如：直接调用当前路径里的一个批处理 call test.bat ，或是要调用的批处理在当前路径向上一级的abc文件夹里 call ..\abc\test.bat ，也可以使用绝对路径找到目标批处理 call D:\abc\test.bat (路径的写法请参阅[前言]里命令 cd 的用法介绍)。当然，一个最直观的例子往往更能说明问题。建立两个批处理(假设他们在同一路径下)"调用.bat"和"被调用.bat"，它们的内容分别为：
::::::::::::调用.bat::::::::::::
@echo off
echo 这里是 调用.bat
pause

call 被调用.bat

echo 现在又回到了 调用.bat
pause
::::::::::::::::::::::::::::::::

:::::::::::被调用.bat:::::::::::
echo 这里是 被调用.bat
pause
::::::::::::::::::::::::::::::::
编辑并保存好这两个批处理，然后运行批处理"调用.bat"，所得到的结果跟我们预期的完全一致。

3.2.3 启动

start 虽然也不是一个简单的命令，但用法绝对不难理解。来几个例子：start msconfig 用来打开"系统配置应用程序"；start notepad 则可以打开一个记事本；start "这就是所谓的标题" cmd 用来打开一个新的命令提示符；start "随便写个标题" http://www.baidu.com 便打开百度的首页；而 start "开玩了" E:\game\starcraft\starcraft.exe 却是开始星际争霸(如果您的电脑里安装了星际且路径与上述一致的话)等等。虽然 start 的参数很多(具体用法在输入 help start 后可以得到)，但通常情况下我们只需要知道 start 后面加上标题，再跟上想要执行程序、命令或网址即可。值得注意的是：标题要用双引号引用起来，否则会被作为可执行的文件来处理；所要执行的东西如果不是系统内部程序或命令的话，则需要我们给出具体的路径，比如绝对路径。
当然，start 也可以打开另外一个批处理。这看起来似乎与 call 相仿，却有一些区别。为了对比 call 和 start 之间的效果差异，可以在上一个例子中修改"调用.bat"中的 call 被调用.bat 为 start 被调用.bat 。从"调用.bat"开始执行后，"被调用.bat"也的确能够被调用。但之前的批处理也同时继续执行着。事实上，此时这两个程序已经完全独立开了，是两个独立的进程。

3.3 参数

上文提到了调用，这里就不得不补充一下参数。何谓参数？假如您要使用命令 dir ，那后面所跟的路径文件名也好、/p (分页显示)也好、/w (宽列表显示)也好、又或者是 /s (所有目录及子目录)也好，这些都能被称作为参数。对于一条命令来说，它除了能返回(输出)给我们一些信息以外，我们还经常给它输入一些信息，被输入的信息就是参数；然而，对于一个批处理来说，它除了能为我们工作(输出结果)以外，有时也需要外界给他一些信息。

3.3.1 参数的传递

为了很好的认识到这一点，我们先稍微修改一下上文所使用的"被调用.bat"这个批处理文件，使之能够接受处理外界给它的输入参数。
:::::::::::被调用.bat:::::::::::
echo 这里是 被调用.bat
echo 您输入的第1条参数为 %1
echo 您输入的第2条参数为 %2
pause
::::::::::::::::::::::::::::::::
其中，%1 和 %2 分别代表运行"被调用.bat"批处理时所跟的两个参数。那么它该如何获得所谓的参数1和参数2呢。双击运行"被调用.bat"当然是不行的了。可以在命令提示符里输入"被调用.bat"的全名，并在后面加上两个参数即可(如果"被调用.bat"不在当前工作路径，需要输入"被调用.bat"的路径，比如绝对路径，以便让计算机找到它)。就像：D:\批处理\test\被调用.bat Tom and Jerry 。运行时我们会发现 %1 和 %2 分别显示为 Tom 和 and ，Jerry 为作为第3个参数来处理，但该批处理中却未用到 %3 。提示：在XP等操作系统中，对于汉字的输入可用 Ctrl + 空格 切换出中文输入法；也可以按 Tab 键让其自动切换并补充完成您所想要输入的路径。

为了进一步验证这一点，我们再改一下批处理"调用.bat"，让它在调用其他批处理时加上参数
::::::::::::调用.bat::::::::::::
@echo off
echo 这里是 调用.bat
pause

call 被调用.bat Hello world!

echo 现在又回到了 调用.bat
pause
::::::::::::::::::::::::::::::::

3.3.2 参数的输入与输出

参数不仅可以是值，也可以是变量。如果是变量的话，它既可以作为输入，也可以作为输出。为此，我们需要分别再改一次"调用.bat"和"被调用.bat"。

::::::::::::调用.bat::::::::::::
@echo off
echo 这里是 调用.bat
pause

set /p Num=请输入一个整数:
set Square=

call 被调用.bat Num Square

echo 现在又回到了 调用.bat ，而且，%Num% 的平方是 %Square% 。
pause
::::::::::::::::::::::::::::::::

:::::::::::被调用.bat:::::::::::
echo 这里是 被调用.bat
echo 您输入的第1条参数为 %1
echo 您输入的第2条参数为 %2

set /a %2 = %1 * %1

echo 经过计算后，您输入的第1条参数为 %1
echo 经过计算后，您输入的第2条参数为 %2
pause
::::::::::::::::::::::::::::::::

可以看出，在批处理"被调用.bat"中的 call 被调用.bat Num Square 里，变量 Num 和 Square 被传递过去的只是变量名而已，而不是变量中的数值。另外，尝试将"调用.bat"中的 call 被调用.bat Num Square 换为 call 被调用.bat %Num% Square ，然后再对比一下结果，相信您一定会有所收获。

3.3.3 函数

在一个批处理的内部调用时，使用参数会怎么样呢？那么这就是函数的雏形。把之前的"跳转.bat"稍微也改一下
::::::::::::跳转.bat::::::::::::
@echo off
call :FirstLable 很好很强大

:SecondLable
echo 然后显示这句
pause
goto :EOF

:FirstLable
echo 首先显示这句，后面跟的参数为 %1
pause
::::::::::::::::::::::::::::::::

对于 goto 所跟的标签或 start 所跟的程序，它们后面能否加参数呢？答案是：前者是否定的；后者是肯定的，试试看。

3.4 后记

写了那么多天，也许我们应该来点更实际更有用的东西。前几天无意中发现了一个163邮箱登录器，在此作为例子介绍一下。

:::::::163邮箱登录器.bat::::::::
@echo off
::不显示命令行
mode con cols=32 lines=8
::设置窗口的尺寸
title 163邮箱登录器
::设置该批处理的标题
color 3a
::设置背景(暗靛色)和文字(亮绿色)的颜色。
::另外，在命令提示符中输入 color/? 可获得详细的颜色信息

set /p username=帐号：
set /p password=密码：
::给出输入的提示，并将字符串赋给相应的变量

start "正在登录邮箱" "https://reg.163.com/logins.jsp?username=%username%&password=%password%&url=http://fm163.163.com/coremail/fcg/ntesdoor2"
::事实上，那个网址链接才是整个程序的核心部分，注意其中的 %username% 和 %password% 分别是指变量 username 和 password 里的字符串内容。
::::::::::::::::::::::::::::::::

# 第四章：条件 循环

4.1 条件 if

4.1.1 if 是一种极其普遍却又非常重要的语句，说得严重点这就是一种能够体现程序灵魂的东西之一。在大多数的编程语言(例如 C VB JScript Java 等)中都能看到 if 的身影。if 语句的功能正如它的字面含义一样——如果。批处理程序的语言格式相比较我们常见的 C 语言来说，并不是那么的严谨，至少看上去是更自由一些。比如 if 在批处理中的具体用法及格式就有很多，使用和发挥的余地也很大，但随之带来的问题就是我们不得不多花一些时间来记忆其各种用法和格式并分辨它们之间的差异。为了简化该问题使之更容易理解，在此我们并不打算过早地接触 if 的全面用法或格式，而是从最基本的用途开始。

4.1.2 在有前几篇文章的学习作基础的情况下，如果您能理解以下几行语句，那么您已经对 if 有了深刻的认识了(其中两个连续的等号 == 表示：是否等于)。
set var=Tom
if %var%==Tom echo It works
if %var%==Jerry echo We will never see this
如果变量 var 的值为 Tom Hanks ，即中间含有空格之类的特殊符号，那么我们在使用 if 时，就得为字符串加上双引号，就像 if "%var%"=="Tom Hanks" echo It works (注意，给字符串加上双引号后，在进行判断的时候会连双引号一起考虑进去。所以，为了使两边的对比均衡，所以一定要在 == 两边的两个字符串上同时都加双引号)。这里也体现了批处理程序语言格式的多样性(如果您熟悉 C 语言格式的话，就知道一串字符总是要被双引号引起来)。不过为了方便记忆，我们在使用 if 的时候，不妨总是在字符串上使用双引号，这样既好阅读，又不容易引起歧异。

::::::::::改变颜色.bat::::::::::
@echo off
echo 您希望字体的颜色是红色还是绿色？

:RETRY
set /p choice=请输入您的选择，R 或者 G ：

if "%choice%"=="R" goto R
if "%choice%"=="r" goto R
if "%choice%"=="G" goto G
if "%choice%"=="g" goto G
goto RETRY

:R
color c
echo 您选择了红色字体
pause
exit

:G
color a
echo 您选择了绿色字体
pause
exit
::::::::::::::::::::::::::::::::
上面的例子能很好地说明了 if 与 goto 的结合使用带来的实用效果。其中，在使用 if 进行判断变量 choice 的值是否为字母 R 或 G 时，分别对其大小写都进行了判断。其实您还可以使用 if 的参数 /i ，就像 if /i "%choice%"=="r" ，这样在进行比较的时候就不区分大小写了。

4.1.3 说到了 if 就不得不说一下 else ，else 无法单独使用，必须与 if 配合连用。
:::::::::else的用法.bat:::::::::
@echo off

if "%TIME:~0,2%" lss "12" (
echo 现在是上午
) else (
echo 现在是下午
)

pause
::::::::::::::::::::::::::::::::
其中，变量 TIME 是动态环境变量之一，表示当前时间(在 set/? 中有介绍)。%TIME:~0,2% 的含义还没忘记吧，意思是取变量 TIME 的前两个字符(忘记的朋友请参阅上一篇[赋值 调用 参数])。lss 是 if 命令扩展用法，表示 小于 的意思。此外，还有等于、不等于、大于、大于等于、小于等于 的缩写，详细信息可以在 if/? 中获得。因此，对于上述批处理的理解就是：如果当前时间(前两位表示小时)小于12(点)的话，那么将显示输出“现在是上午”，否则就显示为“现在是下午”。另外：这里的大小比较判断只是对其ASCII符的大小比较，并不是真正的数值型变量的比较，稍后下文会有关于数值型变量比较的介绍。

对于 if 和 else 的编写格式有较严格的要求，尤其是在两个圆括号上，若以不正确的格式使用可能会导致 if 或 else 等命令无效。虽然上面的编写格式并不是唯一的，但使用统一、固定的格式编写代码会大大提高代码的可读性。为了加深对 if else 的理解，我们可以把上面的批处理扩展一下。
:::::::::else的用法.bat:::::::::
@echo off

if "%TIME:~0,2%" lss "12" (
if "%TIME:~0,2%" lss " 6" (
echo 现在是凌晨
) else (
echo 现在是上午
)
) else (
if "%TIME:~0,2%" lss "18" (
echo 现在是下午
) else (
echo 现在是晚上
)
)

pause
::::::::::::::::::::::::::::::::

4.1.4 刚才提到的数值型变量的比较，其实很简单，就如下面的例子中描述的一样。
::::::::::::::::::::::::::::::::
@echo off
set /a num=5

if %num% == 5 (
echo 变量 num 等于 5
)

if not %num% == 4 (
echo 变量 num 不等于 4
)

set /a num = ( %num% + 3 ) * 2
:: 变量 num 加3并乘2后再赋给变量 num 自身

if %num% == 16 (
echo 经过运算后，现在变量 num 等于16
)

if not %num% == 16 (
echo 此时的变量 num 不会不等于 16 ，因此这一句不会显示了
)

pause
::::::::::::::::::::::::::::::::

4.1.5 延迟变量扩充。考虑到读取一行文本时所遇到的目前扩充的限制时，延迟变量扩充是很有用的，而不是在执行的时候。下面的例子可以很好的说明直接变量扩充与延迟变量扩充的区别。
::::::::延迟变量扩充.bat::::::::
@echo off
setlocal EnableDelayedExpansion

set /a num=5

if %num% == 5 (
set /a num*=3

echo 在 if 语句之前，变量 num 等于 %num%
echo 但变量 num 在经过运算后，且由于延迟变量扩充被启用，变量 num 等于 !num!
)

echo 但最终变量 num 还是等于 %num%

pause
::::::::::::::::::::::::::::::::
if 条件下的两行 echo 在输出变量值的时候用到的符号不一样，一个是用百分号 % 包括起来的，另一个用的却是惊叹号 ! 。虽然在显示 %num% 之前已经使变量 num 的数值乘了3倍，但是由于没有延迟变量的扩充，使得 %num% 的结果仍然是 5 。但用 !num! 显示出的值已经变为 15 了。注意到批处理中的 setlocal EnableDelayedExpansion (setlocal/? 查看相关信息)，这表示开启延迟变量扩充。此时的 !num! 才有意义。不然 !num! 将无法被识别，因为在默认情况下，延迟变量扩充是被停用的。

4.1.6 此外，if 还有其他的用法—— if exist 和 if defined 。if exist 可判断文件是否存在，就像这样：
if exist "D:\test my folder\a.txt" (
del "D:\test my folder\a.txt"
) else (
echo 您所要删除的文件不存在
)
在对文件进行操作之前进行判断其是否存在很有意义，这使得代码更加健壮。

而对于 if defined 来说，与 if exist 类似，只不过 if defined 的判断对象不是文件，而是变量，它用于判断环境变量是否被定义。

4.2 循环 for

4.2.1 如果批处理不具备批量处理的功能，那么它就徒有虚名了。而命令 for ，在某种意义上彻底体现出了批处理的强大快捷省事批量的作用。在看过 for/? 后，可以归纳出 for 大致可以分三种常用的类型(或者叫使用方法)。从针对的循环目标来看，它们分别是针对于文件、数字、以及文字。

4.2.2 for %i in (*.*) do @echo %i 。这就是 for 的一般使用格式。注意到其中的浅靛色文字 for 、in 和 do ，是 for 的固定用法。其内容可以理解为：在某一范围内(in)，对于其中的某一文件来说(for)，做如下的处理(do)。而 for %i in (*.*) do @echo %i 就是在当前工作目录的所有文件中(in (*.*))，对于其中的某一文件(for %i)，做出显示其名称的处理(do @echo %i)。变量 i 仅在当前循环语句 for 里起作用，%i 表示其值。
注意：以上是直接在命令提示符里以命令的形式表达出来的写法；在批处理文件中应使用双百分号 %% 代替单百分比号 % ，就像：%%i。关于它们之间的区别我研究了好半天才分清楚 orz [具体请参阅后文第4.2.5节]。

批量修改文件名是其比较有用的典例之一。看看下面的批处理
:::::::批量修改文件名.bat:::::::
@echo off
setlocal EnableDelayedExpansion
set /a num=1
for %%i in (D:\test\*.txt) do (
ren "%%i" !num!.txt
set /a num+=1
)
::::::::::::::::::::::::::::::::
这个批处理并不难理解。就像第4.1.5节所说的：使用了 setlocal EnableDelayedExpansion 后，可以让 for 或 if 后面的执行语句中变量的值随其变化而不断更新(所以后面使用了 !num! 而不是 %num%)。整个批处理的处理过程就是对 D:\test\*.txt 中的所有文本文件进行批量改名，文件名从 1.txt 开始依次为 2.txt 、3.txt ……。
注意：请确保循环语句 in 路径中的文件不是重要的文件，因为改名后将无法使用撤消，如果像我一样不小心把重要文件误改名的话就又要 orz 了一次。

以上批处理是固定了文件的路径以及文件后缀名。为了增加该批处理的功能，我们可以让用户自己选择要进行改名的文件所在路径，以及选择所进行文件修改的后缀名。当然，有些朋友还希望有给文件批量加上前缀(比如：前缀1.txt 前缀2.txt 等等)。(关于 批量改文件名.bat 在第六章中还有进一步的修改)
::::::::批量改文件名.bat::::::::
@echo off
setlocal EnableDelayedExpansion

set /p zpath=请输入目标文件所在的路径：
set /p prefix=请输入文件名前缀(不能包含以下字符\/:*?"<>|)：
set /p ext=请输入文件的扩展名(例如 .txt)：
set /a num=1

for %%i in (%zpath%\*%ext%) do (
ren "%%i" "%prefix%!num!.%ext%"
set /a num+=1
)
::::::::::::::::::::::::::::::::

4.2.3 也许大家注意到了，上面 for 的用法仅仅是针对多个文件来进行循环重复操作的。如果想对一系列有规律的数字进行循环，或是在一定的次数内对某个操作进行循环重复的执行，使用 for 也能够实现。/l 是可以跟在 for 后面的重要参数之一。比如：for /l %i in (5,3,16) do echo %i ，可以让数值型的变量 i 依次成为：5、8、11、14 。正如 in 里所描述的规律 (5,3,16) 一样，从 5 开始，每次增加 3 ，直到 16为止。同样，我们还可以试一下 for /l %i in (19,-4,3) do echo %i ，这次 i 是递减的规律。很明显，结果将依次显示为：19、15、11、7、3 。

这样的用法很自然的能让我们想到，重复执行N遍完全一样的事情不再是麻烦而又无聊的了。在下面的例子里，您一定会找到惊喜的。
::::::::::圆圈方阵.bat::::::::::
@echo off
setlocal EnableDelayedExpansion

set var=○
for /l %%i in (1,1,7) do set var=%var%!var!
:: 此时变量 var 已经变成一行连续的8个圆圈了

for /l %%i in (1,1,8) do (
echo 这是第 %%i 份>输出结果%%i.txt
for /l %%j in (1,1,8) do echo %var%>>输出结果%%i.txt
)

echo 8 X 8 的 ○ 矩阵已经画好，并保存到8份文本文件里了
pause
::::::::::::::::::::::::::::::::
注意：%%i ，上一节中提到过，在批处理文件中需要用连续的两个百分号 %% 来描述循环变量 i ，而不是一个。
注意：%var% 与 !var! ，它们的用法与区别，在第4.1.5节中有解释。
注意：i 与 j ，在循环里面再套循环时，前一个循环变量 i 在没有释放之前，不应该让第二个循环变量的名称与 i 重复。
注意：> 与 >> ，同样是向某设备里输出，但却有区别，请参阅第2.2节。

4.2.4 for 也可以对指定范围内的文字进行循。for 后面跟参数 /f ，/f 后面跟选项，所指定的范围 in 里可以是一个文件里的文字，可以是一个字符串，也可以是一条命令的输出结果。我们首先以一个文件里的文字作为循环对象，循环时，每一行将被循环一次。
::::::::::文字筛选.txt::::::::::
@echo off
echo 测试 文字筛选.txt 里每一行的首单词
for /f %%i in (文字筛选.txt) do echo %%i
pause

echo.
echo skip=2 表示前两行被跳过
for /f "skip=2" %%i in (文字筛选.txt) do echo %%i
pause

echo.
echo tokens=2,4-6 表示提取每行的第2个、以及第4到6个单词
for /f "skip=2 tokens=2,4-6" %%i in (文字筛选.txt) do echo %%i, %%j, %%k, %%l.
pause

echo.
echo eol=N 表示当此行的首字母为 N 时，就忽略该行
for /f "eol=N skip=2 tokens=2,4-6" %%i in (文字筛选.txt) do echo %%i, %%j, %%k, %%l.
pause

echo.
echo delims=e 表示不再以空格区分每个词，而是以字母 e 作为间隔
for /f "eol=N skip=2 tokens=2,4-6 delims=e" %%i in (文字筛选.txt) do echo %%i, %%j, %%k, %%l.
pause

echo.
echo usebackq 表示双引号里的东西是文件名而不是字符串
for /f "usebackq eol=N skip=2 tokens=2,4-6 delims=e" %%i in ("文字筛选.txt") do echo %%i, %%j, %%k, %%l.
pause
::::::::::::::::::::::::::::::::
作为测试，可以在上述批处理文件的同一路径下创建一个用于测试的文本文件 文字筛选.txt ，其内容为：
Hello there!
This text is an example of test for the batch file 文字筛选.bat.
Notice the first letter in this line, N.
If the eol charactor was set to be letter N.
The third line will not be considered by the batch.

4.2.5 ESCAPE字符 % ，通常被译为转义字符，但也有更形象的译名脱逸字符、逃逸字符等。也就是说 % 不仅仅将与其相关的特定字符串转义并替换为特定字符串，而且自身也会被“脱逸”。而且类似于C语言中的转义字符 \ ，双%会转义并脱逸为单百分号 % ，四%则脱为双百分号 %% 。[3]

注意下面这个批处理中的双百分号 %% 的用法
::::::::::::::::::::::::::::::::
@echo off
set Text=Hello world!
for /l %%i IN (0,1,11) do call echo %%Text:~%%i,1%%
pause
::::::::::::::::::::::::::::::::

# 第五章：组合命令 管道命令

5.1 组合命令

组合命令 & 、&& 和 || 是一类用于两个或多个命令语句之间起衔接作用的符号。这对于我们想一次性执行两条或多条命令，以及前面命令执行结果的成功与否作为后面命令是否被执行的衡量标准，起着决定性的作用。

5.1.1 &

通过紧随的例子，echo Checking what executable files we have in WINDOWS... & dir C:\WINDOWS\*.exe & echo And we got lots of stuff here. 我们不难理解 & 在多个命令之间所起的连接作用。事实上，我们完全可以将这三者分成3行来独立执行，因为它们之间是相互独立的关系。不论三者中每一条命令的结果如何，后面的一条命令总能被得到执行(这是与下文 && 和 || 的不同之处)。

5.1.2 &&

&& 作为组合命令之一，与 & 类似，也有着并列多条命令并将其按顺序执行的功能。与 & 的不同之处，也许此时您已经猜到了，没错，如果多命令中的某一条命令执行出错时，后面的所有命令将不会再被执行；如果一直没有出错则会一直执行完所有的并列命令。为了很好的对比它们之间的区别，我们分别尝试一下下面的两个例子。
echo Checking if we have the following directory... & dir "E:\starcraft II" & echo Seems it does not exist.
echo Checking if we have the following directory... && dir "E:\starcraft II" && echo Seems it does not exist.
它们的区别是一目了然的，前者会有 Seems its not exist. 的输出，而后者却没有。

5.1.3 ||

|| 的用途与 && 的功能恰好相反。当遇到执行正确的命令后将不再执行后面的命令，如果没有出现正确的命令则一直执行完所有命令。例如 dir D:\test || md D:\test ，如果 D:\test 存在，即第一条命令执行正确的话，后面的创建 D:\test 就不会再执行了；相反，如果第一条命令执行出错，那么后面的命令就起作用了。

在混合使用的时候需要注意它们的优先级。分析下面几个例子有助于我们理解它们的执行效果(如果我们的机器上并没有 Z: 盘的话)。注：浅蓝色的命令表示会被执行到，而深蓝色的命令将不会被执行到。
dir Z: &　dir C: || echo Howdy
dir C: &　dir Z: || echo Howdy
dir Z: && dir C: || echo Howdy
dir C: && dir Z: || echo Howdy
dir C: && dir C: || echo Howdy

dir C: || echo Howdy &　echo Hi there
dir C: || echo Howdy && echo Hi there
dir Z: || echo Howdy &　echo Hi there
dir Z: || echo Howdy && echo Hi there
实验一下，看看结果是不是跟预期的一样。

5.2 管道命令

5.2.1 > 、>>

它们是输出重定向命令，在第2.2节中已有详细的介绍。其主要功能就是将一条命令或某个程序输出结果的重定向到特定文件中。> 与 >> 的区别在于，> 会清除调原有文件中的内容后写入指定文件，而 >> 只会追加内容到指定文件中，而不会改动其中的内容。下面将会是一个很有用的例子。

众所周知，System32 文件夹是多数木马潜伏和发作的好地方。当我们刚装好机器的时候，可以给此时机器里还没有病毒、木马的 System32 文件夹里的所有可执行文件(.exe)和动态链接库文件(.dll)作个记录。等以后发觉 System32 里多了可疑的东西的时候再作个记录，然后跟之前的记录对比一下，就很容易发现问题了。
为了方便作记录，我们可以执行类似下面的一条命令：dir %windir%\system32\*.exe>D:\%DATE:~0,10%的exe文件.txt 。其中，%windir% 是当前启动系统所在的目录，默认情况下通常是 C:\WINDOWS ；%DATE:~0,10% 是指当天的日期，比如2007-11-30，如果您没有忘记在3.1.4节里曾描述过的话。而整条命令的结果就是把 System32 里的所有可执行文件名称及信息记录到一个指定的文本文件里了。同理：我们可以记录 System32 里的所有 dll 文件：dir %windir%\system32\*.dll>D:\%DATE:~0,10%的dll文件.txt 。
在经过一段时间后，我们可以再次使用上面两条命令，从而得到两个新的记录文件。然后对比一下两个文件看看有什么差异。DOS 命令里提供了这样一条命令 fc ，它允许我们对两个文件之间的差异进行比较。使用时就像：fc d:\2007-11-30的exe文件.txt d:\2007-12-01的exe文件.txt 。[1]

5.2.2 |

没错，只是一条竖线而已。它可以将它左边命令的输出结果放到它右边的命令里作为输入参数。这种用法据说在 Unix 里很常见。

有个能简单检测机器是否中冰河木马的例子：netstat /a /n | find "7626" && echo 已被冰河感染 || echo 未被冰河感染 。其中：
netstat 用于显示当前的网络连接情况，参数 /a 显示所有连接和监听端口；/n 以数字形式显示地址和端口号。仅仅执行 netstat /a /n 后，您将会看到输出的结果为：各种协议下的本地和目标的地址及端口，以及它们的连接状态。
命令 find 则可以搜索指定的字符串，在指定的文件中。netstat /a /n 的输出结果将通过 | 成为命令 find 的第二个参数。因此整个的一条命令可以理解为：在网络连接状态的输出结果中，查找字符串 7626 ，如果查找成功的话，将输出被感染的提示，否则便提示未感染。&& 和 || 请参考第5.1.3节的例子。(端口 7626 是冰河所使用的默认端口。事实上，这并不是一个严谨的检测冰河木马存在的方法，但它却是说明组合命令和管道命令一个很好的例子)

5.2.3 管道命令还有 < 、<& 和 >& ，它们并不常见，在此暂时不讨论了。

# 第六章：常用实例 上

6.1 批量修改文件名

在第4.2.2节中，我们已经会使用循环命令对大量文件改名进行批量处理。但总结一下，该批处理并不是很健壮。判断一个程序的好坏，往往不是站在程序员的角度，而从用户的角度出发。比如：在用户使用它的时候，如果输入了不正确的路径格式怎么办？如果输入了含有非法符号的前缀怎么办？输入的扩展名也有问题怎么办？改完名后看不到是否执行成功的反馈信息，等等。带着这些想法，我们将原程序再次修改一下。

:::::::批量修改文件名.bat:::::::
@echo off
title 批量修改文件名
setlocal EnableDelayedExpansion
:: 启用延迟变量扩充

:GetPath
set zpath=%CD%
:: 对变量进行初始化，防止用户不输入而直接跳过。其中%CD%表示当前路径
set /p zpath=请输入目标文件所在的路径：
if %zpath:~0,1%%zpath:~-1%=="" set zpath=%zpath:~1,-1%
:: 检查变量 zpath 的第一个和最后一个字符是否为 "" ，是的话就去掉
if not exist "%zpath%" goto :GetPath
:: 如果 zpath 值的路径不存在，就得跳转回去，要求重新输入

:GetPrefix
set prefix=未命名
set /p prefix=请输入文件名前缀(不能包含以下字符\/:*?"<>|)：
for /f "delims=\/:*?<>| tokens=2" %%i in ("z%prefix%z") do goto :GetPrefix
:: 这里对变量 perfix 进行检查，发现有非法符号便跳转到 :GetPrefix
:: 事实上，这里并没有对双引号 " 进行检测，因为双引号无法在此被转义为可用的分隔符
:: 即使是在这个程序里，不正确地使用双引号也会引起程序异常而退出。
:: 因此，想把它做的非常人性化并不是一件容易的事情

:GetExt
set ext=.*
set /p ext=请输入文件的扩展名(不输入则表示所有类型)：
if not "%ext:~0,1%"=="." set ext=.%ext%
:: 检查变量 ext 的第一个是否为句点 . ，不是的话就加上
:: 建议这里对变量 ext 也检查一下，发现有除*外的非法符号便跳转到 :GetExt

set answer=N
echo.
echo 您试图将 %zpath%\ 里的所有 %ext% 类型的文件以 %prefix% 为前缀名进行批量改名，是否继续？
set /p answer=继续请输入 Y ，输入其它键放弃...
if "%answer%"=="Y" goto :ReadyToRename
if "%answer%"=="y" goto :ReadyToRename

echo 放弃文件改名，按任意键退出... & goto :PauseThenQuit

:ReadyToRename

set /a num=0
echo.

if "%ext%"==".*" (
for %%i in ("%zpath%\*%ext%") do (
set /a num+=1
ren "%%i" "%prefix%!num!%%~xi" || echo 文件 %%i 改名失败 && set /a num-=1
)
) else (
for %%i in ("%zpath%\*%ext%") do (
set /a num+=1
ren "%%i" "%prefix%!num!%ext%" || echo 文件 %%i 改名失败 && set /a num-=1
)
)

if %num%==0 echo %zpath%\ 里未发现任何文件。按任意键退出... & goto :PauseThenQuit

echo 文件改名完成，按任意键退出...

:PauseThenQuit
pause>nul
::::::::::::::::::::::::::::::::


相对第4.2.2节里的批量修改文件的批处理来说，已经全面多了。不过这仍然有许多地方需要进一步完善，比如，输出的文件名编号可以用001、002、003这样的方式来表达，以便浏览器在以文件名排列文件时能按我们或需要的顺序进行排列。

========================================朴实的分割线========================================

6.2 批量备份进程映像列表以及注册表自启动项

什么是备份；为什么要备份；怎么去备份；备份些什么，说起来我们可能会更关心这些问题。
什么是备份：将某事物复制出额外一份完全一样的事物，并妥善保存起来的过程；
为啥要备份：当原事物出现异常或无法使用的时候，取出复制品并代替原来无法使用的事物；
怎么去备份：复制，与原事物完全一样地去复制，然后保存到安全的地方；
备份些什么：系统、文档、数据库、工程、记录、进度等等。
不过，这些都不是本文的主旨。

本节的写作起因是从《利用Windows系统自带命令手工搞定病毒》这篇文章开始的。这篇文章的主旨是：用 tasklist 备份好进程列表→通过 fc 比较文件找出病毒→用 netstat 判断进程→用 ntsd 终止进程→搜索找出病毒以及同伙文件并删除→用 reg 命令修复注册表。
不过，这些也不是本文的主旨。

在前面提到的《手工杀毒》一文中，第二步提到：如果感觉机器异常，可以将现有的进程与以前机器正常时的进程加以对比，看看是否多出了可疑的进程。这就意味着您必须得记忆或保留住以前正常时的进程映像名，即备份。备份时正如《手工杀毒》中所说的，在系统正常且刚进入Windows的时候就做一个进程映像名列表的备份。查看机器当前的进程可以通过组合键 Ctrl+Alt+Del 召唤出"Windows 任务管理器"，然后切换到"进程"页即可。对于如何记录下当前的这些进程，您可以用 PrintScreen 键抓图(Alt+PrintScreen 可以仅抓取当前窗口的图)并以图片的形式保存，当然，您甚至可以简单地将这些映像名抄到一张纸上。本文所提供的方法要比抓图或是手抄的方法更先进一些，至少是更严肃了一些。

除了 Windows 任务管理器 以外，使用命令 tasklist 也可以看到(详细信息请参阅 tasklist/?)当前进程。tasklist>进程.txt 即可将进程以表格的形式输出到一个文本文件中。在输出结果中除了进程映像名以外，还有 PID 、会话、内存使用等信息，但后面的这些信息并不总是固定的，因此我们也并不需要这些。我们所关心的只是一个按照字母顺序排列的进程映像名清单，以便今后进行比较。

::::::备份进程和自启动.bat::::::
@echo off

set TempFolder=临时文件夹
:: 设置临时文件夹的名称
if not exist %TempFolder% md %TempFolder%
:: 创建临时文件夹
echo.>%TempFolder%\temp.tmp
:: 在临时文件夹里创建一个临时文件 temp.tmp ，并清空其内容

set ExportImageName=%cd%\进程映像列表%date:~0,10%.txt
:: 设置默认导出文件的路径以及文件名
set /p ExportImageName=所要导出的进程映像名称列表备份文件名：
:: 用户自定义输入的路径文件名

for /f "delims=," %%i in ('tasklist /nh /fo csv') do echo %%~i>>%TempFolder%\temp.tmp
:: 将 tasklist 中的进程映像名输出到临时文件 temp.tmp 中 [注1]
sort %TempFolder%\temp.tmp>"%ExportImageName%"
:: 将进程映像名按字母顺序排列
del %TempFolder%\temp.tmp
:: 删除临时文件夹里的文件 temp.tmp
echo 当前进程中的所有映像名已导出到以下文件：%ExportImageName%
pause
:::::::: 以上完成了进程备份，下面开始备份自启动的注册表信息

set ExportRegRunName=%cd%\注册表自启动%date:~0,10%.txt
:: 设置默认导出文件的路径以及文件名
set /p ExportRegRunName=所要导出的注册表自启动备份文件名：
:: 用户自定义输入的路径文件名

reg export HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run %TempFolder%\HKLMrun.reg
reg export HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run %TempFolder%\HKLMexp.reg
reg export HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run %TempFolder%\HKCUrun.reg
reg export HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run %TempFolder%\HKCUexp.reg
:: 将相关的注册表信息导出到各个临时的注册表文件中 [注2]

copy %TempFolder%\*.reg "%ExportRegRunName%">nul
:: 将临时文件夹里所有的注册表文件合并复制到一个文件中
del %TempFolder%\*.reg
:: 删除临时文件夹里所有的临时注册表文件
if exist %TempFolder% rd %TempFolder%
:: 删除临时文件夹
echo 当前自启动的注册表信息已导出到以下文件：%ExportRegRunName%
pause
::::::::::::::::::::::::::::::::

注1. tasklist /nh /fo csv 中参数 /nh 表示不输出栏标头，参数 /fo csv 表示以双引号包含字符串，并用逗号分隔各个字符串。for /f "delims=," %%i in ('tasklist /nh /fo csv') do echo %%~i>>a.txt 表示在无栏标头且以 csv 格式输出的 tasklist 结果中，以逗号为分隔符，将每行的首字符串依次输出到文本文件 a.txt 中。

注2. reg export 能将注册表指定项的所有子项和值导出到指定的文件中(请参阅 reg/? 与 reg export /?)。当然，以上4个只是常见的自启动键值，病毒或木马所在注册表中添加或修改的项不仅此而已，更多需要备份的项可用类似的方法自行添加。

对于查找可以进程的方法，与前文 5.2.1 小节中所提到的对比系统文件夹找差异的过程类似，使用命令 fc 对比两个不同时期的进程映像名列表，找出多余的可疑进程(如果您无法确定某个进程是干什么用的或者是否存在安全风险，可以先到网上搜索并了解一下，比如：进程知识库)。至于是用 taskkill 还是 ntsd 来终止可以的进程，怎样用属性加时间来查找并锁定可以的文件，以及 reg import 注册表导入恢复的用法，这些仍然不是本文的重点。[创作日期：2008-01-08]

========================================朴实的分割线========================================

6.3 批量查看同一子网络下的所有IP在线情况[编辑中]

本小节的批处理可以让您知道自己所在局域网的同一网段下都有哪些IP被使用了。不得不承认，我在创造这个批处理的时候想法很奇怪，甚至有些愚蠢。

:::::::查看所有子网IP.bat:::::::
@echo off
title 查看所有子网IP

set /a Online=0
set /a Offline=0
set /a Total=256
set ExportFile=子网IP在线统计.txt
:: 初始化在线IP与不在线IP的个数为零，共扫描256个IP，结果输出的文件名

set StartTime=%time%
:: 记录程序的开始时间

for /f "delims=: tokens=2" %%i in ('ipconfig /all ^| find /i "IP Address"') do set IP=%%i
:: 获得本机IP [注1]

if "%IP%"=="" echo 未连接到网络 & pause & goto :EOF
if "%IP%"==" 0.0.0.0" echo 未连接到网络 & pause & goto :EOF
:: 当IP为空或 0.0.0.0 时，提示未连接并退出该程序

for /f "delims=. tokens=1,2,3,4" %%i in ("%IP%") do (
set /a IP1=%%i
set /a IP2=%%j
set /a IP3=%%k
set /a IP4=%%l
)
:: 以句点为分隔符，分别将IP的四个十进制数赋给四个变量

set /a IP4=0
echo 在线的IP：>%ExportFile%
:: 初始化IP的第四个数值为零，并创建结果输出文件

:RETRY
ping %IP1%.%IP2%.%IP3%.%IP4% -n 1 -w 200 -l 16>nul && set /a Online+=1 && echo %IP1%.%IP2%.%IP3%.%IP4%>>%ExportFile% || set /a Offline+=1
:: ping 目标IP [注2]

set /p =[将本文底部评论4中的退格符替换到此处]<nul
set /a Scanned=%Online%+%Offline%
set /a Progress=(%Online%+%Offline%)*100/%Total%
set /p =正在扫描：%Scanned%/%Total% 扫描进度：%Progress%%%<nul
:: 删除当前行的内容，并重新显示进度信息 [注3]

set /a IP4+=1
if %IP4% lss %Total% goto :RETRY
:: 当IP的第四个数值小于总数时，跳转回 :RETRY 处，重复执行直到全部 ping 完为止

echo.
echo.

set EndTime=%time%
:: 记录程序的结束时间

set /a Seconds = %EndTime:~6,2% - %StartTime:~6,2%
set /a Minutes = %EndTime:~3,2% - %StartTime:~3,2%
if %Seconds% lss 0 set /a Seconds += 60 & set /a Minutes -= 1
if %Minutes% lss 0 set /a Minutes += 60
:: 计算时间差

set /a Percent=%Online%*100/(%Online%+%Offline%)
:: 计算在线百分比

echo 在线IP个数: %Online%
echo 不在线IP个数: %Offline%
echo 在线百分比: %Percent%%%
echo 统计耗时: %Minutes%分%Seconds%秒
echo 统计日期: %date% %time:~0,-3%
echo.>>%ExportFile%
echo 在线IP个数: %Online%>>%ExportFile%
echo 不在线IP个数: %Offline%>>%ExportFile%
echo 在线百分比: %Percent%%%>>%ExportFile%
echo 统计耗时: %Minutes%分%Seconds%秒>>%ExportFile%
echo 统计日期: %date% %time:~0,-3%>>%ExportFile%
echo 记录已保存到文件"%ExportFile%"中
::显示结果并将结果保存到文件中
pause
::::::::::::::::::::::::::::::::

注1. ipconfig 是内置于 Windows 的 TCP/IP 应用程序，用于显示本地计算机网络适配器的物理地址和IP地址等配制信息，这些信息一般用来检验手动配置的 TCP/IP 设置是否正确。当在网络中使用 DHCP 服务时， ipconfig 可以检测到计算机中分配到了什么IP地址，是否配置正确，并且可以释放，重新获取IP地址。这些信息对于网络测试和故障排除都有重要的作用。[3]
更详细的说明请参阅 ipconfig/? 。ipconfig /all ，参数 /all 表示查看详细的网络配置。命令 ipconfig /all ^| find /i "IP Address" 表示在 'ipconfig /all 的结果中，以 "IP Address" 为查找对象，进行搜索(其结果类似于：IP Address. . . . . . . . . . . . : 10.30.11.51 )。
而整条命令中的 for 语句，则表示在上述结果中，以冒号为间隔(delims=:)，查找第2个字串(tokens=2)。很明显，所找到的结果就是自己电脑当前的IP地址了(如果您只有一快网卡或是只启用了一个网卡的话。显然，对于多个网卡会显示出多个IP的情况，我并没有考虑的太全面)。[关于 for 更详细请参阅 4.2.4 小节]
另外，注意到在 ipconfig /all ^| find /i "IP Address" 中有一个转义字符 ^ ，它的作用是让后面的管道命令 | 生效，而不是让程序把 | 误解为 for 语句里参数的一部分。

注2. ping 其实才是本批处理的核心部分。命令 ping 的主要作用是通过发送数据包并接收应答信息来检测两台计算机之间的网络是否连通。比如我可以输入 ping 10.30.11.35 以便查看我是否能与我所在的局域网中IP为 10.30.11.35 的机器连通。如果我不懂批处理的话，也许我就得从 IP 10.30.11.1 开始，挨个地 ping 到 IP 10.30.11.255 ，才能达到我在本小节的最初目的。
在批处理中 ping 的3个参数 -n 1 -w 200 -l 16 分别表示：仅 ping 一遍[-n 1]，等待200毫秒后按超时考虑[-w 200]，发送16字节的数据[-l 16]。
另外，此命令行中同时用到了两个 && 和一个 || 的组合命令，我不得不承认这种复杂的逻辑关系会给您带来阅读上的困难。

注3. 这里使用了 set /p =显示内容<nul 来显示一些内容，是因为这中方式显示出内容后并不换行，而 echo 却不行。还有向上数4行的那一堆奇怪的符号，表示的是退格符号，能删除掉当前行中以显示的内容。


图6-3 查看所有子网IP.bat 的运行结果
本小节的使用程度并不大，却很有趣，至少并没有想象中的那么愚蠢。[创作日期：2008-01-10]

========================================朴实的分割线========================================

6.4 令人大囧的WGA，华丽地卸载之

WGA 全称 Windows Genuine Advantage ，是微软制造的反盗版软件，因其自动潜入系统而备受争议。当用户访问 Windows Update 服务以及微软网站的下载页面时，该计划的附属检测软件就会被请求安装。很多用户都是在不知情的情况下被安装上了WGA。事实上，安装了WGA后，正版的用户并没见得有什么优势，但盗版用户的劣势绝对会被发挥的淋漓尽致。如果您是盗版的受害者(尽管您更坚持认为自己是WGA的受害者)，那么建议您仔细阅读一下本小节。首先，卸载方法在微软的帮助与支持中有详细英文说明，中文版的在百度知道里也有介绍。不过，这些依然不是本文的主旨，我们更关心的还是批处理。

::::::::::WGA卸载器.bat:::::::::
@echo off
title WGA卸载器
setlocal EnableDelayedExpansion

set /a step=1
if exist WGA卸载记录.txt (
for /f "tokens=2" %%i in (WGA卸载记录.txt) do set /a step=%%i+1 & goto :Step!step!
)
:: 查看记录进行到第几步了

:Step1
:RenameFiles
if exist %Windir%\system32\wgalogon.old del %Windir%\system32\wgalogon.old
if exist %Windir%\system32\wgatray.old del %Windir%\system32\wgatray.old
:: 检查相关的临时文件是否已存在，若存在则删之
Ren %Windir%\system32\WgaLogon.dll WgaLogon.old
if %errorlevel% neq 0 goto :Abort
Ren %Windir%\system32\WgaTray.exe WgaTray.old
if %errorlevel% neq 0 goto :Abort
:: 将相关文件改名，如果操作失败则中断程序
call :WriteUninstallStatus
:: 将卸载情况记录到文件中
echo 步骤一完成。已重命名文件 WgaLogon.dll 和 WgaTray.exe。
ping -n 2 127.0>nul
goto :RebootPrompt
:: 需要重启计算机

:Step2
:UnregisterServer
Regsvr32 %Windir%\system32\LegitCheckControl.dll /u
:: 将相关的服务注册撤消
call :WriteUninstallStatus
:: 将卸载情况记录到文件中
echo 步骤二完成。已撤消服务 LegitCheckControl.dll。
ping -n 2 127.0>nul
goto :RebootPrompt
:: 需要重启计算机

:Step3
:DeleteFiles
Del %Windir%\system32\wgalogon.old
Del %Windir%\system32\WgaTray.old
Del %Windir%\system32\LegitCheckControl.dll
:: 将相关的文件删除
call :WriteUninstallStatus
:: 将卸载情况记录到文件中
echo 步骤三完成。已删除文件 wgalogon.old WgaTray.old 和 LegitCheckControl.dll。
ping -n 2 127.0>nul

:Step4
:DeleteRegistrySubkeys
set /a step=4
reg delete "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Notify\WgaLogon" /f
reg delete "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\WgaNotify" /f
:: 将相关的子项从注册表中删除
call :WriteUninstallStatus
echo 步骤四完成。已删除注册表中相关的子项。
:: 将卸载情况记录到文件中
ping -n 2 127.0>nul

:Step5
:UninstallDoneSuccessfully
echo.
echo 已完成对WGA的卸载!
del WGA卸载记录.txt
pause>nul
exit

::::以下为程序所调用到的函数::::

:WriteUninstallStatus
:: 该函数用于将当前卸载情况记录到文本文件中
echo WGA卸载已完成第 %step% 步>WGA卸载记录.txt
set /p =更改文件名称：<nul >>WGA卸载记录.txt
call :IsCompleted %step%
set /p =撤消服务注册：<nul >>WGA卸载记录.txt
call :IsCompleted %step%
set /p =删除相关文件：<nul >>WGA卸载记录.txt
call :IsCompleted %step%
set /p =清除注册信息：<nul >>WGA卸载记录.txt
call :IsCompleted %step%
goto :EOF

:IsCompleted
:: 该函数用于判断各个卸载步骤的完成情况
if %1 gtr 0 (
echo 已完成>>WGA卸载记录.txt
set /a step-=1
) else (
echo 未完成>>WGA卸载记录.txt
)
goto :EOF

:RebootPrompt
set /a TimerTick=9
echo.
echo 需要重启计算机才能继续下一步。
echo 请在计算机重启后再运行该批处理，以便继续完成对WGA的卸载。
set /p choice=是否现在就重启? [Y/N]
if "%choice%"=="y" shutdown -r -t 15 -c 因卸载WGA的需要而重启& exit
if "%choice%"=="Y" shutdown -r -t 15 -c 因卸载WGA的需要而重启& exit
echo 稍后请手动重启计算机。
pause>nul
exit

:Abort
echo 程序中止。
echo.
echo 您确信您已经安装了WGA?
pause>nul
exit
::::::::::::::::::::::::::::::::

# 第七章：常用实例 下

如果您已从头至尾完整地忍受过了前六章的基础，那么就让我们来做一些更疯狂的批处理吧……

7.1 坐在家里周游世界

没错，我想是认真的，对于任何您想去往地球上的地点，您所需要做的仅仅是提供一个目的地的经纬度坐标而已。当然，我是不会给您提供去往世界各地的签证和机票的，但是海量的卫星照片还是能让您过足了瘾的。此时您手头可能并没有足够的坐标资源，不过我这里"恰好"有些陈芝麻烂谷子，是当年在留园网上搜集的地理坐标，具体请参阅《关于Google Maps的趣点》。这里必须得先感谢卫星图片的提供者 Google Maps ，因为你知道，毕竟航拍卫星并不是人人都能买的起的。

本小节也是在我回顾《关于Google Maps的趣点》这篇文章开始的。因为当年在搜集这些该死的地理坐标时，偷了一些懒，结果有些是小数格式的，有些是度分秒格式的，查看起来并不方便。如果有 Google Earth 来转换它们之间的格式倒也不难。但我知道，此时您的迅雷网快电驴里已经排满了各种各样电影、游戏、动漫的下载任务，看来您并没有下载 Google Earth 的意思。没关系，下面这个批处理多少能让您更方便地浏览 Google Maps 上的卫星照片。

::::::坐在家里周游世界.bat::::::
@echo off
title 坐在家里周游世界
:: 设置标题
:Start
cls
:: 清屏
set choice=1
set /p choice=请选择经纬度格式(1. 小数格式 2. 度分秒格式 3. 退出)：
:: 选择经纬度的格式 或 退出程序
if %choice%==3 goto :EOF
if %choice%==2 goto :DMSFormat

:DecimalFormat
:: 小数格式的经纬度处理
set latitude=39.906477
set longitude=116.391467
:: 初始化为伟大首都天安门的坐标
set /p latitude=纬度：
set /p longitude=经度：
:: 提示用户输入目标的经纬度 [注1]
goto :LaunchMap

:DMSFormat
:: 度分秒格式的经纬度处理
set "DMSlatitude=39 54 23 N"
set /a degree=39
set /a minute=54
set /a second=23
set NorthOrSouth=N
:: 初始化为美丽首都天安门度分秒格式的纬度
echo.
set /p DMSlatitude=纬度(格式 [度] [分] [秒] [N ^| S])：
:: 提示用户输入目标的纬度 [注2]
for /f "tokens=1,2,3,4,5" %%i in ("%DMSlatitude%") do (
set degree=%%i
set minute=%%j
set second=%%k
set NorthOrSouth=%%l
if "%%l"=="" echo 不正确的格式 & goto :DMSFormat
)
:: 分别获得纬度的度、分、秒，以及南半球或北半球
if %degree% lss 0 echo 纬度必须大于0度 或不正确的格式 & goto :DMSFormat
if %degree% gtr 90 echo 纬度必须小于90度 或不正确的格式 & goto :DMSFormat
if %minute% lss 0 echo 纬度必须大于0分 或不正确的格式 & goto :DMSFormat
if %minute% gtr 60 echo 纬度必须小于60分 或不正确的格式 & goto :DMSFormat
if %second% lss 0 echo 纬度必须大于0秒 或不正确的格式 & goto :DMSFormat
if %second% gtr 60 echo 纬度必须小于60秒 或不正确的格式 & goto :DMSFormat
:: 判断纬度的度、分、秒格式是否有效 [注3]
set /a degree*=3600
set /a minute*=60
set /a second=%degree%+%minute%+%second%
set /a latitude=%second%*2500/9
:: 将度分秒计算并转换为小数格式 [注4]
if %NorthOrSouth%==N goto :LatitudeLockDown
if %NorthOrSouth%==n goto :LatitudeLockDown
if %NorthOrSouth%==S set /a latitude=0-%latitude% & goto :LatitudeLockDown
if %NorthOrSouth%==s set /a latitude=0-%latitude% & goto :LatitudeLockDown
:: 判断南北半球格式是否有效
echo 南北半球标识不明确，请使用 N 或 S 来表示，不区分大小写。 & goto :DMSFormat

:LatitudeLockDown
set "DMSlongitude=116 23 29 E"
set /a degree=116
set /a minute=23
set /a second=29
set EastOrWest=E
:: 初始化为可爱首都天安门度分秒格式的经度
echo.
set /p DMSlongitude=经度(格式 [度] [分] [秒] [E ^| W])：
:: 提示用户输入目标的经度
for /f "tokens=1,2,3,4" %%i in ("%DMSlongitude%") do (
set degree=%%i
set minute=%%j
set second=%%k
set EastOrWest=%%l
if "%%l"=="" echo 不正确的格式 & goto :LatitudeLockdown
)
:: 分别获得经度的度、分、秒，以及东半球或西半球
if %degree% lss 0 echo 经度必须大于0度 或不正确的格式 & goto :LatitudeLockDown
if %degree% gtr 180 echo 经度必须小于180度 或不正确的格式 & goto :LatitudeLockDown
if %minute% lss 0 echo 经度必须大于0分 或不正确的格式 & goto :LatitudeLockDown
if %minute% gtr 60 echo 经度必须小于60分 或不正确的格式 & goto :LatitudeLockDown
if %second% lss 0 echo 经度必须大于0秒 或不正确的格式 & goto :LatitudeLockDown
if %second% gtr 60 echo 经度必须小于60秒 或不正确的格式 & goto :LatitudeLockDown
:: 判断经度的度、分、秒格式是否有效
set /a degree*=3600
set /a minute*=60
set /a second=%degree%+%minute%+%second%
set /a longitude=%second%*2500/9
:: 将度分秒计算并转换为小数格式
if %EastOrWest%==E goto :LongitudeLockDown
if %EastOrWest%==e goto :LongitudeLockDown
if %EastOrWest%==W set /a longitude=0-%longitude% & goto :LongitudeLockDown
if %EastOrWest%==w set /a longitude=0-%longitude% & goto :LongitudeLockDown
:: 判断东西半球格式是否有效
echo 东西半球标识不明确，请使用 E 或 W 来表示，不区分大小写。 & goto :LatitudeLockDown

:LongitudeLockDown
set latitude=%latitude:~0,-6%.%latitude:~-6%
set longitude=%longitude:~0,-6%.%longitude:~-6%
:: 整理纬度和经度

:LaunchMap
echo.
set /a zoom=16
set /p zoom=放缩度(0~18 默认值：%zoom%)：
:: 提示用户输入照片的放缩值
echo.
echo 正在打开 纬度：%latitude% 经度：%longitude% 的卫星照片...
start "正在打开Google Maps..." "http://maps.google.com/?t=k&z=%zoom%&ll=%latitude%,%longitude%"
:: 将放缩值和经纬度值作为 Google Maps 链接参数，打开相应的照片 [注5]

pause
goto :Start
::::::::::::::::::::::::::::::::

注1. 纬度或经度尽量能精确到小数点后3位数以上，因为越精确的坐标越能准确地帮您找到目标的位置

注2. 度分秒格式的纬度(或经度)您大概并不陌生，如果高中时代的您没有选择在地理课上逃课的话。例如 39°54' 23.32" N 就表示北纬39度54分23.32秒。另外，正在上高中的朋友在政治课上可以适当地翘课，个人研究表明，政治这玩意学多了不利于青少年大脑的发育。

注3. 纬度不能超过90度，而经度不能超过180度，分和秒的范围是0~59，这些常识是绝不会难到您的。

注4. 经纬度从度分秒格式转换为小数格式只需要：(度*60*60+分*60+秒)/60/60 即可，北纬39度54分23.32秒转换为小数即39.906477度。事实上，此处latitude的值是实际纬度的一百万倍，因为DOS命令中并不支持浮点型(实数)的变量，不用担心，在后面会有小数点向前移动6位的处理。同时，希望您也没有在数学课上翘课的习惯。

注5. 该链接正指向此时经纬度和放缩值的卫星地图，其中具体参数的含义可以参考《关于Google Maps的趣点》文中的解释。

好吧，您可能已经迫不及待地想试试这东西了。那么在运行该批处理后，首先您会得到选择两种经纬度类型的提示。选1的话，只需要分别输入小数格式的纬度和精度，以及放缩值即可(如果您还不确定放缩值是啥东西的话，可以置空直接使用默认值)。
如果在程序的一开始选择了2，也就是度分秒格式的经纬度。比如我们的目的地是：北纬15°17' 55" ，东经19°25' 47" ，您可以依次在纬度和经度里输入 15 17 55 n 和 19 25 47 e ，然后在放缩值里填上 22 。这样您就能看到北非中部一个小村庄里的几位村民，以及他们的奶牛和骆驼。
![img](http://docs.30c.org/dosbat/chapter07/1.gif)

坐在家里周游世界.bat 的运行界面
![img](http://docs.30c.org/dosbat/chapter07/2.gif)

坐在家里周游世界.bat 的运行结果

事实上，上面的照片是 Google Maps 中罕见的几张高清卫星照片之一，并不是每张照片的放缩值都能达到23滴，因为你也知道，即使是能买得起航拍卫星的家伙，也是没有足够的资金和精力来把地球的每一个角落都拍得一清二楚的。

========================================朴实的分割线========================================

7.2 进程分析者

写了一篇很简单却又很占篇幅的玩意，被我称之为"进程分析者"。此批处理的构思很轻松，只是简单地使用 tasklist 列出所有的进程，再显示为容易理解的文字说明而已。这与任务管理器中的进程相比，除了易于识别以外，还能帮您鉴别出那些喜欢"偷梁换柱"的隐患进程。比如用肉眼去观察 winhlep.exe 或 winhe1p.exe 的时候很容易忽视它们，而使用"进程分析者"却不会。

:::::::::进程分析者.bat:::::::::
@echo off
setlocal enabledelayedexpansion

title 进程分析者
set SPACE=
set /a NumOfTotal=0
set /a NumOfSafe=0
set /a NumOfNasty=0
set /a NumOfUnknown=0
set IconOfSafe=√
set IconOfNasty=×
set IconOfUnknown=？

:::::::: 以下定义为可信任的进程，可自定义更多的扩充 ::::::::
:: 1. 系统进程
set alg.exe=%IconOfSafe%处理Windows网络连接共享和网络连接防火墙[系统进程]
set csrss.exe=%IconOfSafe%管理Windows图形相关任务[系统进程]
set explorer.exe=%IconOfSafe%用于显示系统桌面的图标,任务栏等[系统进程]
set lsass.exe=%IconOfSafe%用于本地安全和登陆策略[系统进程]
set services.exe=%IconOfSafe%管理启动和停止服务[系统进程]
set smss.exe=%IconOfSafe%用于对话管理子系统调用和系统对话操作[系统进程]
set spoolsv.exe=%IconOfSafe%用于将打印机任务发送到本地打印机[系统进程]
set svchost.exe=%IconOfSafe%用于执行动态链接库DLL文件[系统进程]
set System=%IconOfSafe%[系统进程]
set taskmgr.exe=%IconOfSafe%任务管理器，用于显示系统正在运行的进程[系统进程]
set winlogon.exe=%IconOfSafe%用于处理系统的登陆和登陆过程[系统进程]
set winmgmt.exe=%IconOfSafe%用于系统管理员创建WIndows管理脚本[系统进程]
:: 2. 基本进程
set cmd.exe=%IconOfSafe%Windows系统的命令行程序
set msimn.exe=%IconOfSafe%OutlookExpress相关程序
set mspaint.exe=%IconOfSafe%画图板
set notepad.exe=%IconOfSafe%记事本
set wab.exe=%IconOfSafe%通讯薄，用于储存地址、联系人和Email
set ctfmon.exe=%IconOfSafe%提供语音识别、手写识别等
set conime.exe=%IconOfSafe%输入法编辑器相关程序
set SOUNDMAN.EXE=%IconOfSafe%Realtek声卡相关程序
set tasklist.exe=%IconOfSafe%这是本批处理的核心所在-_-b
set wmiprvse.exe=%IconOfSafe%用于通过WinMgmt.exe程序处理WMI操作
:: 3. 工作进程
set EXCEL.EXE=%IconOfSafe%Excel
set WINWORD.EXE=%IconOfSafe%Word
set XDICT.EXE=%IconOfSafe%金山词霸
set sqlservr.exe=%IconOfSafe%用于SQL基础服务
set wmplayer.exe=%IconOfSafe%Windows Media Player
set Mplayerc.exe=%IconOfSafe%暴风影音
set WinRAR.exe=%IconOfSafe%WinRAR
:: 4. 防护进程
set 360tray.exe=%IconOfSafe%360安全卫士实时监控程序
set AntiArp.exe=%IconOfSafe%ARP防火墙
set CCenter.exe=%IconOfSafe%瑞星信息中心
set RavMonD.exe=%IconOfSafe%瑞星监控程序
set rfwsrv.exe=%IconOfSafe%瑞星个人防火墙相关程序
set RavStub.exe=%IconOfSafe%瑞星杀毒软件相关程序
set RfwMain.exe=%IconOfSafe%瑞星防火墙主程序
set RavTask.exe=%IconOfSafe%瑞星定时杀毒程序
set RavMon.exe=%IconOfSafe%瑞星监控程序
:: 5. 网络进程
set iexplore.exe=%IconOfSafe%IE浏览器
set Maxthon.exe=%IconOfSafe%傲游浏览器
set BaiduHi.exe=%IconOfSafe%百度Hi
set msmsgs.exe=%IconOfSafe%MSN网络聊天工具
set QQ.exe=%IconOfSafe%腾迅QQ
set TXPlatform.exe=%IconOfSafe%腾迅平台
set Thunder5.exe=%IconOfSafe%迅雷下载
set Skype.exe=%IconOfSafe%Skype语音聊天
set Contentfilter.exe=%IconOfSafe%Skype的相关程序
set skypePM.exe=%IconOfSafe%Skype语音聊天

:::::::: 以下定义为已知的危险进程，可自定义更多的扩充 ::::::::
set a.exe=%IconOfNasty%蠕虫
set av.exe=%IconOfNasty%蠕虫
set blss.exe=%IconOfNasty%木马/拨号器
set cmd32.exe=%IconOfNasty%病毒
set crss.exe=%IconOfNasty%蠕虫
set csrse.exe=%IconOfNasty%病毒/木马
set Desktop.exe=%IconOfNasty%木马/病毒/间谍
set directs.exe=%IconOfNasty%蠕虫
set dllhlp.exe=%IconOfNasty%木马
set dllreg.exe=%IconOfNasty%病毒
set explore.exe=%IconOfNasty%灰鸽子
set explored.exe=%IconOfNasty%蠕虫
set optimize.exe=%IconOfNasty%拨号器/广告
set pcsvc.exe=%IconOfNasty%间谍
set rundll16.exe=%IconOfNasty%木马
set run32dll.exe=%IconOfNasty%间谍
set scvhost.exe=%IconOfNasty%木马/广告
set svchosts.exe=%IconOfNasty%木马
set system32.exe=%IconOfNasty%木马
set updater.exe=%IconOfNasty%蠕虫
set web.exe=%IconOfNasty%病毒/木马
set win32.exe=%IconOfNasty%病毒
set windows.exe=%IconOfNasty%蠕虫
set winlogin.exe=%IconOfNasty%病毒/木马
set winstart.exe=%IconOfNasty%间谍/广告
set wintsk32.exe=%IconOfNasty%病毒
set winupdate.exe=%IconOfNasty%病毒
set winxp.exe=%IconOfNasty%病毒
set winhlep.exe=%IconOfNasty%病毒

:::::::: 以下定义为未知的进程 ::::::::
set UnknownTask=%IconOfUnknown%未识别的进程

:: 程序开始
echo 进程名称 分析结果
echo.

for /f "tokens=1" %%i in ('tasklist /NH') do (
set TaskName=%%i%SPACE%
set TaskName=!TaskName:~0,20!
if defined %%i (
echo !TaskName! !%%i!
if "!%%i:~0,1!"=="%IconOfNasty%" (
set /a NumOfNasty+=1
)
) else (
echo !TaskName! %UnknownTask%
set /a NumOfUnknown+=1
)
set /a NumOfTotal+=1
)
echo ________________________________________________________________
echo.
echo 共 %NumOfTotal% 个进程。
if %NumOfNasty% gtr 0 (
echo %NumOfNasty% 个存在安全隐患的进程！
)
if %NumOfUnknown% gtr 0 (
echo %NumOfUnknown% 个未知进程。
)
pause>nul
::::::::::::::::::::::::::::::::

结果：


图7-3 进程分析者.bat 的运行结果

分析完毕！

========================================朴实的分割线========================================

7.3 公元2738年11月28日是星期几[编写中]

公元2738和11月28日，是个好日子。我打赌您不知道这天究竟是星期几而且您也并不想知道。

:::公元2738-11-28是星期几.bat:::[β版]
@echo off
setlocal enabledelayedexpansion

:Initialization
:: 初始化
set TargetDate=%date:~0,4%%date:~5,2%%date:~8,2%
set /a Year = 0 & rem 年 范围: 1~9999
set /a Mon = 0 & rem 月 范围: 1~12
set /a Day = 0 & rem 日 范围: 1~28 29 30 31
set /a IsLeapYear = 0 & rem 是否闰年 范围: 0~1

:PromptEntering
:: 提示输入日期
set /p TargetDate=请输入日期(格式: YYYYMMDD 例如: %TargetDate%):

:: 转换为有效的年月日[注1]
if %TargetDate:~0,3% == 000 (
set /a Year = %TargetDate:~3,1%
) else (
if %TargetDate:~0,2% == 00 (
set /a Year = %TargetDate:~2,2%
) else (
if %TargetDate:~0,1% == 0 (
set /a Year = %TargetDate:~1,3%
) else (
set /a Year = %TargetDate:~0,4%
)
)
)
if %TargetDate:~4,1% == 0 (
set /a Mon = %TargetDate:~5,1%
) else (
set /a Mon = %TargetDate:~4,2%
)
if %TargetDate:~6,1% == 0 (
set /a Day = %TargetDate:~7,1%
) else (
set /a Day = %TargetDate:~6,2%
)

:CheckLeapYear
:: 检测是否是闰年[注2]
set /a DivisionBy4 = %Year%%%4
set /a DivisionBy100 = %Year%%%100
set /a DivisionBy400 = %Year%%%400

if %DivisionBy4% == 0 set /a IsLeapYear = 1 & rem 能被4整除的是闰年
if %DivisionBy100% == 0 set /a IsLeapYear = 0 & rem 能被100整除的非闰年
if %DivisionBy400% == 0 set /a IsLeapYear = 1 & rem 能被400整除的是闰年

set /a Month1 = 31
set /a Month2 = 28 + %IsLeapYear%
set /a Month3 = 31
set /a Month4 = 30
set /a Month5 = 31
set /a Month6 = 30
set /a Month7 = 31
set /a Month8 = 31
set /a Month9 = 30
set /a Month10= 31
set /a Month11= 30
set /a Month12= 31

:: 检测范围是否有效[注3]
if %Year% lss 1 echo 年份应该大于0 & goto :Initialization
if %Year% gtr 9999 echo 年份不能超过9999 & goto :Initialization
if %Mon% lss 1 echo 月份不能小于1 & goto :Initialization
if %Mon% gtr 12 echo 月份不能大于12 & goto :Initialization
if %Day% lss 1 echo 日数不能小于1 & goto :Initialization
if %Day% gtr 31 echo 日数不能大于31 & goto :Initialization
if %IsLeapYear% == 0 (
if %Mon%%Day% == 229 echo %Year%年的2月没有29日 & goto :Initialization
)
if %Day% gtr !Month%Mon%! echo %Mon%月没有%Day%日 & goto :Initialization

:: 开始计算天数
set /a Year -= 1 & rem 该年未结束，应减一年
set /a Day = %Day% + Year * 365 & rem 一年365天
set /a Day = %Day% + Year/4 & rem 每4年多一闰
set /a Day = %Day% - Year/100 & rem 可每100年少一闰
set /a Day = %Day% + Year/400 & rem 但每400年还多一闰

set /a Mon -= 1 & rem 该月未结束，应减一月
for /l %%i in (1,1,%Mon%) do (
set /a Day = !Day! + !Month%%i! & rem 累计前几月的天数
)

:: 计算星期
set /a Week = %Day%%%7 & rem 除7得余数
set WeekChars=日一二三四五六
set Week=!WeekChars:~%Week%,1! & rem 换成汉字

:: 显示结果
echo.
echo %TargetDate:~0,4%年%TargetDate:~4,2%月%TargetDate:~6,2%日，是公元第%Day%天，星期%Week%
echo ___________________________________________
echo. & pause>nul & goto :Initialization
::::::::::::::::::::::::::::::::

注1 正如第三章关于 set 为变量赋予数值型的值所说的，如果数值是以 0 开头的，那么该数值便是八进制的。这并不是我们所期望，因此对变量的首位数非零的检测是必要的。

注2 闰年每隔四年来一次，这是众所周知的，但它并不完全正确。因为一年约为365.24219天，因此闰年将遵循于“四年一闰,百年不闰,四百年再闰”的规则。

注3 每个月的天数并不固定，但它们都在28~31这个范围内。

公元2738年11月28日是星期一，跟 Garfield 一样，我也讨厌星期一。

========================================朴实的分割线========================================

7.4 163邮箱登录器之不显示密码篇

还记得我们在3.4节中所提到过的163信箱登录的问题吗，那是一个不错的小批处理。不过那个批处理存在着一个小小的缺憾：在输入密码时，密码会暴露无遗地直接显示在屏幕上，这对于注重个人隐私的您来说，显然是无法接受的。

:::::::163邮箱登录器.bat::::::::
@echo off
title 163邮箱登录器
mode con cols=80 lines=25
::设置窗口的尺寸

set /p username=用户名:
cls

chcp 437>nul
graftabl 936>nul
:: 转换代码页编号为 936

echo 用户名: %username%
set /p =密　码: <nul

echo hP1X500P[PZBBBfh#b##fXf-V@`$fPf]f3/f1/5++u5x>in.com
:: 创建一个神奇的二进制可执行文件
for /f "tokens=*" %%i in ('in.com') do set password=%%i
:: 在那个神奇的文件被执行完返回结果之前，不显示任何东西
del in.com

setlocal EnableDelayedExpansion
for /l %%i in (0,1,255) do (
if not "!password:~%%i,1!"=="" (
set /p =*<nul
) else (
endlocal
goto :LoginMail
)
)
endlocal
:: 计算密码长度，然后显示相应个数的星号

:LoginMail

start "正在登录邮箱" "https://reg.163.com/logins.jsp?username=%username%&password=%password%&url=http://fm163.163.com/coremail/fcg/ntesdoor2"

echo.
echo 正在登录邮箱...
ping -n 2 127.0>nul
:: 等待一小段时间
::::::::::::::::::::::::::::::::

备注：本小节尚存在问题待解决(输入密码时使用退格会被当作字符记录下来，不输入任何东西则将显示Invalid keyboard code specified)……

# 第八章：番外篇

标题很奇怪？其实，您可以把它当作一期OVA。

8.1 批量十六进制二进制格式转换

想把数据(流)以十六进制或二进制的形式显示出来？UltraEdit之类的编辑软件一定是首选。即使是要自己亲自转出来，C/C++等语言也会方便的多。如果您跟我一样选择使用批处理来实现的话，那么很好，很有挑战性。

::::::DataFormatConvert.bat:::::
@echo off

:Initialization
set TempFile=temp.tmp
set /a num = 0
set BinaryFormat=Bin
:: 默认为二进制数字0或1显示
set ConvertOption=ConvertToHex
:: 默认为十六进制转换
set ShowProgress=ShowProgressOn
:: 默认为显示转换进度
set BackSpace=[将本文底部评论3中的退格符替换到此处]
:: 退格符

set Source=z%1
:: 添加一个临时字符 z
if %Source:~1,1%z%Source:~-1%=="z" set Source=z%Source:~2,-1%
:: 检查变量参数1的第一个和最后一个字符是否为 "" ，是的话就去掉
set Source=%Source:~1%
:: 去掉临时字符 z
if "%Source%"=="" goto :HelpInformation
if "%Source%"=="/?" goto :HelpInformation
if /i "%Source%"=="/help" goto :HelpInformation
if not exist "%Source%" echo 目标文件不存在 & exit /b 2
:: 检查参数1 [注1]

if /i "%2"=="/Bin" set ConvertOption=ConvertToBin
if /i "%3"=="/Bin" set ConvertOption=ConvertToBin
if /i "%2"=="/Block" set ConvertOption=ConvertToBin & set BinaryFormat=BinBlock
if /i "%3"=="/Block" set ConvertOption=ConvertToBin & set BinaryFormat=BinBlock
if /i "%2"=="/ProgressOff" set ShowProgress=ShowProgressOff
if /i "%3"=="/ProgressOff" set ShowProgress=ShowProgressOff
:: 检查参数2和3 [注2]

for %%i in ("%Source%") do (
set SourceDrivePathName=%%~dpni
set FileSize=%%~zi
)
:: 获得源文件的 驱动器号+路径+标题名 ，以及文件大小。 d - drive, p - path, n - name, z - size
if "%FileSize%"=="0" echo 目标文件为空 & exit /b 3
del %TempFile% >nul 2>nul
fsutil file createnew %TempFile% %FileSize% >nul
:: 创建一个大小与源文件一样的空白文件，该文件里的所有字节均为0x00

goto :%ConvertOption%

:ConvertToHex
:: 十六进制转换
setlocal EnableDelayedExpansion
set OutputFile="%SourceDrivePathName%.Hex.txt"
echo 文件 %Source% 的十六进制格式:>%OutputFile%
echo. & echo 正在转换为十六进制...

for /f "skip=1 tokens=1,3" %%i in ('fc /b %TempFile% "%Source%"') do (
set index=0x%%i
set index=!index:~0,-1!
set /a offset = !index! - !num!

for /l %%n in (1,1,!offset!) do (
set /p=00<nul>>%OutputFile%
set /a num += 1
)
set /p=%%j<nul>>%OutputFile%
set /a num += 1
call :%ShowProgress% !num!
)
:: 通过与大小相同内容空白的文件进行二进制对比，获得源文件的十六进制码 [注3]
endlocal
goto :ExitSuccess

:ConvertToBin
setlocal EnableDelayedExpansion
set OutputFile="%SourceDrivePathName%.%BinaryFormat%.txt"
echo 文件 %Source% 的二进制格式:>%OutputFile%
echo. & echo 正在转换为二进制...

for /f "skip=1 tokens=1,3" %%i in ('fc /b %TempFile% "%Source%"') do (
set index=0x%%i
set index=!index:~0,-1!
set /a offset = !index! - !num!

for /l %%n in (1,1,!offset!) do (
call :HexTo%BinaryFormat% 0
call :HexTo%BinaryFormat% 0
set /a num += 1
)
set HexData=%%j
call :HexTo%BinaryFormat% !HexData:~0,1!
call :HexTo%BinaryFormat% !HexData:~1,1!
set /a num += 1
call :%ShowProgress% !num!
)
endlocal
goto :ExitSuccess

:HexToBin
:: 函数: HexToBin 用途: 以0或1的形式显示
if %1==0 set /p=0000<nul>>%OutputFile%
if %1==1 set /p=0001<nul>>%OutputFile%
if %1==2 set /p=0010<nul>>%OutputFile%
if %1==3 set /p=0011<nul>>%OutputFile%
if %1==4 set /p=0100<nul>>%OutputFile%
if %1==5 set /p=0101<nul>>%OutputFile%
if %1==6 set /p=0110<nul>>%OutputFile%
if %1==7 set /p=0111<nul>>%OutputFile%
if %1==8 set /p=1000<nul>>%OutputFile%
if %1==9 set /p=1001<nul>>%OutputFile%
if %1==A set /p=1010<nul>>%OutputFile%
if %1==B set /p=1011<nul>>%OutputFile%
if %1==C set /p=1100<nul>>%OutputFile%
if %1==D set /p=1101<nul>>%OutputFile%
if %1==E set /p=1110<nul>>%OutputFile%
if %1==F set /p=1111<nul>>%OutputFile%
goto :EOF

:HexToBinBlock
:: 函数: HexToBinBlock 用途: 以　或■的形式显示[注3]
if %1==0 set /p=　　　　<nul>>%OutputFile%
if %1==1 set /p=　　　■<nul>>%OutputFile%
if %1==2 set /p=　　■　<nul>>%OutputFile%
if %1==3 set /p=　　■■<nul>>%OutputFile%
if %1==4 set /p=　■　　<nul>>%OutputFile%
if %1==5 set /p=　■　■<nul>>%OutputFile%
if %1==6 set /p=　■■　<nul>>%OutputFile%
if %1==7 set /p=　■■■<nul>>%OutputFile%
if %1==8 set /p=■　　　<nul>>%OutputFile%
if %1==9 set /p=■　　■<nul>>%OutputFile%
if %1==A set /p=■　■　<nul>>%OutputFile%
if %1==B set /p=■　■■<nul>>%OutputFile%
if %1==C set /p=■■　　<nul>>%OutputFile%
if %1==D set /p=■■　■<nul>>%OutputFile%
if %1==E set /p=■■■　<nul>>%OutputFile%
if %1==F set /p=■■■■<nul>>%OutputFile%
goto :EOF

:ShowProgressOn
:: 函数: ShowProgressOn 用途: 显示转换进度
set /a mod = %1 %% 50
if %mod% equ 0 (
set /a percent = %1 * 100 / %FileSize%
set /p=%BackSpace%%BackSpace%%BackSpace%<nul
set /p=!percent!%%<nul
)
goto :EOF

:ShowProgressOff
:: 函数: ShowProgressOff 用途: 不显示转换进度
goto :EOF

:HelpInformation
:: 该批处理的帮助信息
echo 将文件转换为十六进制或二进制的格式。
echo.
echo DataFormatConvert source [/Hex ^| /Bin ^| /Block] [/ProgressOn ^| /ProgressOff]
echo.
echo source 指定要转换的文件。
echo /Hex 表示转换为十六进制格式(默认)。
echo /Bin 表示转换为二进制格式。
echo /Block 表示转换为二进制格式并以方块的形式显示。
echo /ProgressOn　显示转换进度(默认)。
echo /ProgressOff 关闭显示进度。
exit /b 1

:ExitSuccess
:: 成功完成并退出
del %TempFile% >nul
set /p=%BackSpace%%BackSpace%%BackSpace%%BackSpace%<nul
echo 转换完成!
exit /b 0
::::::::::::::::::::::::::::::::

注1 exit 的参数 /b ，可以退出当前批处理脚本而不退出调用它的 CMD.EXE。如果从一个批处理脚本外执行，则会退出 CMD.EXE 。exit 的第二个参数 exitCode 是一个数字号码，如果使用了参数 /b ，这个数字号码将成为该批处理退出的 ErrorLevel 。如果退出 CMD.EXE ，则用那个数字设置过程退出代码。

注2 看到该批处理这些可使用的参数，您可能已经发现了，该批处理可以作为一条外部命令来使用，如果您把它放到 %SystemRoot%\system32 或 %SystemRoot% 路径下的话。默认情况下，%SystemRoot%\system32 和 %SystemRoot% 都是环境变量 PATH 的值之一(在 我的电脑->属性->高级->环境变量 中可以查看并设置相关环境变量)。

注3 源文件通过与其大小相同内容全为0x00的文件进行对比后，可以将源文件中所有与0x00不同的字节内容以十六进制码的形式表达出来。同时，还能得到每个不同字节所在的字节数位置，通过这个也便确定了源文件中0x00的内容。

正如注2中所说的，如果该批处理被放到了环境变量 PATH 中的路径中，则它可以作为外部命令来为您工作。
![img](http://docs.30c.org/dosbat/chapter08/1.gif)

DataFormatConvert 的执行示意

十六进制或二进制转换成功的文件将被写到与源文件相同的路径中。
![img](http://docs.30c.org/dosbat/chapter08/2.gif)

经DataFormatConvert 十六进制转换后的文件
对于计算机而言，十六进制码(或者说0和1)才能表达出它们自己的想法，尽管这些对我们来说犹如天书一般。

========================================朴实的分割线========================================

8.2 别挤，自启动的排队来

被放入到自启动项里的程序，从某种意义上来说，在被开启的时候确实简化了用户的操作。然而，在开机后众多的程序就像春运时期挤火车一样的蜂拥而上，这并不是我们所期望的。请不要问我为什么给这个批处理起了个如此无理的名称，所有放在 C:\WINDOWS 下的批处理我都会以小写字母 z 打头，方便管理。

::::::::::zLauncher.bat:::::::::
@echo off
setlocal enabledelayedexpansion
title Launching...
set /a ShortDelay = 6
set BackSpace=[将本文底部评论3中的退格符替换到此处]

set /p choice=LaunchOptions:
if not "%choice%"=="" goto :CustomLaunch

:BasicLaunch
call :LaunchItem1
call :LaunchItem2
call :LaunchItem3
call :LaunchItem4
call :LaunchItem5
goto :EOF

:CustomLaunch
for /l %%i in (0 1 9) do (
set "choice_=!choice:~%%i,1!"
if "!choice_!"=="" echo All Launched! & goto :EOF
if !choice_! gtr 9 echo Unknown Define & goto :EOF
if !choice_! lss 0 echo Unknown Define & goto :EOF
call :LaunchItem!choice_!
)

:LaunchItem1
start "OE" "C:\Program Files\Outlook Express\msimn.exe"
call :IsItemLaunchedSuccessful OE
goto :EOF
:LaunchItem2
start "Skype" "D:\Program Files\Skype\Phone\Skype.exe" /nosplash /minimized
call :IsItemLaunchedSuccessful Skype
goto :EOF
:LaunchItem3
Start "QQ" "D:\Program Files\Tencent\QQ\QQ.exe"
call :IsItemLaunchedSuccessful QQ
goto :EOF
:LaunchItem4
start "BaiduHi" /min "D:\Program Files\baidu\Baidu Hi\BaiduHi.exe"
call :IsItemLaunchedSuccessful BaiduHi
goto :EOF
:LaunchItem5
start "Thunder" /min "D:\Program Files\Thunder Network\Thunder\Thunder.exe"
call :IsItemLaunchedSuccessful Thunder
goto :EOF
:LaunchItem6
start "Tudou" /min "D:\Program Files\Tudou\iTudou\iTudou.exe"
call :IsItemLaunchedSuccessful Tudou
goto :EOF
:LaunchItem7
start "MSN" /min "C:\Program Files\MSN Messenger\msnmsgr.exe"
call :IsItemLaunchedSuccessful MSN
goto :EOF

:IsItemLaunchedSuccessful
set /p =Launching %1<nul & title Launching %1
if ERRORLEVEL 0 (
for /l %%i in (1,1,4) do (
ping -n %ShortDelay% 127.1>nul
set /p =.<nul
)
)
for /l %%i in (1,1,32) do set /p =%BackSpace%<nul
echo %1 Launched
title %1 Launched
ping -n %ShortDelay% 127.1>nul
goto :EOF
::::::::::::::::::::::::::::::::

看得出来，这是一个科技含量很低的批处理，仅仅是在 start 每个程序之间将其挂起一段时间来避免众多程序同时启动所带来的负荷。当然，为了使它能够发挥作用，您得亲自配置它所要启动的程序，以及程序所在的路径才行。

最近在学批处理 ，就需要用到脚本

一.特点

1.通常脚本都是.bat 或.cmd后缀

2.批处理的编程能力远不如C语言等编程语言，也十分的不规范

3.但它还是具有简单的编程能力，可以用if ，for，goto

4.它对大小写不敏感

5.每个编写好的批处理文件都相当于一个DOS的外部命令，把它所在的目录放在DOS搜索路径（path）中，即可在任意位置运行

6.它编译起来方便，任意文本编辑器都可以完成，能帮我们处理平常些机械重复的工作。（这还涉及到定时操作，稍后讲）

二.语法

1.echo 指令与 PHP 的 echo 指令类似，都是用于字符串的输出，echo off表示在此语句后所有运行的命令都不显示命令行本身

　　

 

2、@与echo off相象，但它是加在每个命令行的最前面，表示运行时不显示这一行的命令行（只能影响当前行）　　

　　

3.%[1-9]表示参数，参数是指在运行批处理文件时在文件名后加的以空格(或者Tab)分隔的字符串。 变量可以从%0到%9，%0表示批处理命令本身，其它参数字符串用 %1 到 %9 顺序表示。

 call test2.bat "hello" "haha" (执行同目录下的“test2.bat”文件，并输入两个参数) 
在“test2.bat”文件里写: 
echo %1 (打印: "hello") 
echo %2 (打印: "haha") 
echo %0 (打印: test2.bat) 
echo %19 (打印: "hello"9)


4.Rem 命令 语法：Rem Message... (小技巧：用::代替rem) 注释命令，在C语言中相当与/*...*/,它并不会被执行，只是起一个注释的作用，便于别人阅读和自己日后修改。

  Sample：@Rem Here is the description.
5.Pause 命令 会暂停批处理的执行并在屏幕上显示Press any key to continue...的提示，等待用户按任意键后继

  Sample：
   @echo off
   :begin
   copy a:*.* d:\back
   echo Please put a new disk into driver A
   pause
   goto begin
在这个例子中，驱动器 A 中磁盘上的所有文件均复制到d:\back中。显示的信息提示您将另一张磁盘放入驱动器 A 时，pause 命令会使程序挂起，以便您更换磁盘，然后按任意键再次复制。
6.Call 命令 语法: call [[Drive:][Path] FileName [BatchParameters]] [:label [arguments]] 参数: [Drive:][Path] FileName 指定要调用的批处理程序的位置和名称。filename 参数必须具有 .bat 或 .cmd 扩展名。 调用另一个批处理程序，并且不终止父批处理程序。 如果不用call而直接调用别的批处理文件，那么执行完那个批处理文件后将无法返回当前文件并执行当前文件的后续命令。 call 命令接受用作调用目标的标签。如果在脚本或批处理文件外使用 Call，它将不会在命令行起作用。

  Sample：call="%cd%\test2.bat" haha kkk aaa    (调用指定目录下的 test2.bat，且输入3个参数给他)
  Sample：call test2.bat arg1 arg2    (调用同目录下的 test2.bat，且输入2个参数给他)
 注：可以调用自身(死循环、递归)
7.start 命令 调用外部程序，所有的 DOS命令 和 命令行程序 都可以由 start命令 来调用。

常用参数： MIN 开始时窗口最小化

                   SEPARATE 在分开的空间内开始 16 位 Windows 程序
    
                   HIGH 在 HIGH 优先级类别开始应用程序
    
                   REALTIME 在 REALTIME 优先级类别开始应用程序
    
                   WAIT 启动应用程序并等候它结束 parameters 这些为传送到命令/程序的参数

  Sample：start /MIN test2.bat arg1 arg2    (调用同目录下的 test2.bat，且输入2个参数给他，且本窗口最小化)
  Sample：e:\"program files"\极品列车时刻表\jpskb.exe  (文件路径名有空格时)
 start 是执行的意思，可以用它去做很多事



该脚本调用ConsoleApplication2.exe,并将参数"parameter1" "parameter2"传给exe

ConsoleApplication2.exe的功能是将参数输出在控制台，执行的结果是：



8.If 命令 if 表示将判断是否符合规定的条件，从而决定执行不同的命令。有三种格式: 1) IF 语法: if [not] "参数" == "字符串" 待执行的命令 参数如果等于(not表示不等，下同)指定的字符串，则条件成立，运行命令，否则运行下一句。(注意是两个等号)

   Sample: if "%1" == "a" format a:
   Sample: if {%1} == {} goto noparms
  2) if exist
     语法: if [not] exist [路径\]文件名 待执行的命令
     如果有指定的文件，则条件成立，运行命令，否则运行下一句。
     Sample: if exist config.sys edit config.sys   (表示如果存在这文件，则编辑它，用很难看的系统编辑器)
     Sample: if exist config.sys type config.sys   (表示如果存在这文件，则显示它的内容)
          sample：if not exist "F:\a"   mkdir F:\a   （如果不存在a文件夹就建一个）

 

  3) if errorlevel number
     语法: if [not] errorlevel <数字> 待执行的命令
     如果程序返回值等于指定的数字，则条件成立，运行命令，否则运行下一句。(返回值必须按照从大到小的顺序排列)
     Sample:
       @echo off
       XCOPY F:\test.bat D:\
       IF ERRORLEVEL 1 (ECHO 文件拷贝失败
       ) Else IF ERRORLEVEL 0 ECHO 成功拷贝文件
       pause
     很多DOS程序在运行结束后会返回一个数字值用来表示程序运行的结果(或者状态)，称为错误码errorlevel或称返回码。
     常见的返回码为0、1。通过if errorlevel命令可以判断程序的返回值，根据不同的返回值来决定执行不同的命令。
  4) else
     语法： if 条件 (成立时执行的命令) else (不成立时执行的命令)
     如果是多个条件，建议适当使用括号把各条件包起来，以免出错。
     Sample: if 1 == 0 ( echo comment1 ) else if 1==0 ( echo comment2 ) else (echo comment3 )
     注：如果 else 的语句需要换行，if 执行的行尾需用“^”连接，并且 if 执行的动作需用(括起来)，否则报错
     Sample: if 1 == 0 ( echo comment1 ) else if 1==0 ( echo comment2 ) ^
             else (echo comment3 )
  5) 比较运算符:
     EQU - 等于   (一般使用“==”)
     NEQ - 不等于 (没有 “!=”,改用“ if not 1==1 ”的写法)
     LSS - 小于
     LEQ - 小于或等于
     GTR - 大于
     GEQ - 大于或等于
9.choice 命令 choice 使用此命令可以让用户输入一个字符(用于选择)，从而根据用户的选择返回不同的 errorlevel， 然后配合 if errorlevel 选择运行不同的命令。

注意：choice命令为DOS或者Windows系统提供的外部命令，不同版本的choice命令语法会稍有不同，请用choice /?查看用法。 choice 使用此命令可以让用户输入一个字符，从而运行不同的命令。

使用时应该加/c:参数，c:后应写提示可输入的字符，之间无空格。它的返回码为1234……

    Sample:  choice /c:dme defrag,mem,end
    将显示:  defrag,mem,end[D,M,E]?
    Sample:
    choice /c:dme defrag,mem,end
    if errorlevel 3 goto defrag (应先判断数值最高的错误码)
    if errorlevel 2 goto mem
    if errotlevel 1 goto end
10.for 命令

for 命令是一个比较复杂的命令，主要用于参数在指定的范围内循环执行命令。

1) for {%variable | %%variable} in (set) do command [command-parameters] %variable 指定一个单一字母可替换的参数。变量名称是区分大小写的，所以 %i 不同于 %I 在批处理文件中使用 FOR 命令时，指定变量建议用 %%variable而不要用 %variable。 (set) 指定一个或一组文件。可以使用通配符。 command 指定对每个文件执行的命令。 command-parameters 为特定命令指定参数或命令行开关。

2) 如果命令扩展名被启用，下列额外的 FOR 命令格式会受到支持:

a.FOR /D %variable IN (set) DO command [command-parameters] 如果集里面包含通配符，则指定与目录名匹配，而不与文件名匹配。

b.FOR /R [[drive:]path] %variable IN (set) DO command [command-parameters] 检查以 [drive:]path 为根的目录树，指向每个目录中的FOR 语句。 如果在 /R 后没有指定目录，则使用当前目录。如果集仅为一个单点(.)字符，则枚举该目录树。

c.FOR /L %variable IN (start,step,end) DO command [command-parameters] 该集表示以增量形式从开始到结束的一个数字序列。 如：(1,1,5) 将产生序列 1 2 3 4 5； 而(5,-1,1) 将产生序列 (5 4 3 2 1)。

d.有或者没有 usebackq 选项: FOR /F ["options"] %variable IN (file-set) DO command FOR /F ["options"] %variable IN ("string") DO command FOR /F ["options"] %variable IN (command) DO command

参数"options"为:

eol=c - 指一个行注释字符的结尾(就一个,如“;”)

skip=n - 指在文件开始时忽略的行数。

delims=xxx - 指分隔符集。这个替换了空格和跳格键的默认分隔符集。

tokens=x,y,m-n                 - 指每行的哪一个符号被传递到每个迭代的 for 本身。这会导致额外变量名称的分配。

                                             m-n格式为一个范围。通过 nth 符号指定 mth。
    
                                             如果符号字符串中的最后一个字符星号，那么额外的变量将在最后一个符号解析之后分配并接受行的保留文本。

usebackq - 指定新语法已在下类情况中使用: 在作为命令执行一个后引号的字符串并且一个单引号字符为文字字符串命令并允许在 filenameset中使用双引号扩起文件名称。

3) Sample:

1. 如下命令行会显示当前目录下所有以bat或者txt为扩展名的文件名。 for %%c in (*.bat *.txt) do (echo %%c)

a. 如下命令行会显示当前目录下所有包含有 e 或者 i 的目录名。 for /D %%a in (*e* *i*) do echo %%a

b. 如下命令行会显示 E盘test目录 下所有以bat或者txt为扩展名的文件名。 for /R E:\test %%b in (*.txt *.bat) do echo %%b for /r %%c in (*) do (echo %%c) :: 遍历当前目录下所有文件

c. 如下命令行将产生序列 1 2 3 4 5 for /L %%c in (1,1,5) do echo %%c

d. 以下两句，显示当前的年月日和时间 For /f "tokens=1-3 delims=-/. " %%j In ('Date /T') do echo %%j年%%k月%%l日 For /f "tokens=1,2 delims=: " %%j In ('TIME /T') do echo %%j时%%k分

e. 把记事本中的内容每一行前面去掉8个字符 setlocal enabledelayedexpansion for /f %%i in (zhidian.txt) do ( set atmp=%%i set atmp=!atmp:~8! if {!atmp!}=={} ( echo.) else echo !atmp! ) :: 读取记事本里的内容(使用 delims 是为了把一行显示全,否则会以空格为分隔符) for /f "delims=" %%a in (zhidian.txt) do echo.%%a

4) continue 和 break 利用 goto 实现程序中常用的 continue 和 break 命令, 其实非常简单 continue: 在 for 循环的最后一行写上一个标签，跳转到这位置即可 break: 在 for 循环的外面的下一句写上一个标签，跳转到这位置即可 Sample: (伪代码) for /F ["options"] %variable IN (command) DO ( ... do command ... if ... goto continue if ... goto break ... do command ... :continue ) :break

11.set 语句设置变量赋值

set y=%date:~0,4%
set m=%date:~5,2%
set d=%date:~8,2%

以上是将系统的年月日赋值给y，m，d

12 exp是导出语句

sample ：exp username/password@databasename owner=username file=导出数据名.dmp  log=导出日志名.log

13.将导出数据压缩

"C:\Program Files\WinRAR\WinRAR.exe" a -df 压缩包名.rar 目标文件名.* -r

三.win7系统中如何设置任务实现自动运行程序

开始->所有程序->附件->系统工具->任务计划程序->(右边)操作栏->创建基本任务->名称等填写
————————————————

**第一章 批处理基础**

**第一节 常用批处理内部命令简介**

批处理定义：顾名思义，批处理文件是将一系列命令按一定的顺序集合为一个可执行的文本文件，其扩展名为BAT或者CMD。这些命令统称批处理命令。

小知识：可以在键盘上按下`Ctrl+C`组合键来强行终止一个批处理的执行过程。

了解了大概意思后,我们正式开始学习.先看一个简单的例子!

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `"欢迎来到脚本之家!"``pause`
```

把上面的3条命令保存为文件test.bat或者test.cmd然后执行,
他就会在屏幕上显示以下二行话:

> 欢迎来到脚本之家!

请按任意键继续. . .
这就是一个简单批处理文件了，这个批处理文件一共就用了2条命令 "echo" 和"pause" 还有一个特殊符号"@"
从上面这个简单的批处理中,我们可以发现其实批处理就是运用一些含有特殊意义的符号和一些完成指定功能的命令组合而成,那么在批处理中有多少这样的特殊符号和功能命令呢？我们现在就来仔细了解一下一些最常用的!

(以下内容来源网络,请各位仔细阅读,好进入下节的实例说明)

**目录**

批处理的常见命令（未列举的命令还比较多，请查阅帮助信息）

1、REM 和 ::
2、ECHO 和 @
3、PAUSE
4、ERRORLEVEL
5、TITLE
6、COLOR
7、mode 配置系统设备
8、GOTO 和 :
9、FIND
10、START
11、assoc 和 ftype
12、pushd 和 popd
13、CALL
14、shift
15、IF
16、setlocal 与 变量延迟
17、ATTRIB 显示或更改文件属性

**介绍命令**

**1、REM 和 ::**

REM为注释命令，一般用来给程序加上注解，该命令后的内容不被执行，但能回显。
其次, :: 也可以起到rem 的注释作用, 而且更简洁有效; 但有两点需要注意：
第一, 任何以冒号:开头的字符行, 在批处理中都被视作标号, 而直接忽略其后的所有内容。
有效标号：冒号后紧跟一个以字母数字开头的字符串，goto语句可以识别。
无效标号：冒号后紧跟一个非字母数字的一个特殊符号，goto无法识别的标号，可以起到注释作用，所以 :: 常被用作注释符号，其实 :+ 也可起注释作用。
第 二, 与rem 不同的是, ::后的字符行在执行时不会回显, 无论是否用echo on打开命令行回显状态, 因为命令解释器不认为他是一个有效的命令行, 就此点来看, rem 在某些场合下将比 :: 更为适用; 另外, rem 可以用于 config.sys 文件中。

行内注释格式：%注释内容% （不常用，慎用）

**2、ECHO 和 @**

@字符放在命令前将关闭该命令回显，无论此时echo是否为打开状态。

echo命令的作用列举如下：
（1）打开回显或关闭回显功能
格式:echo [{ on|off }]
如果想关闭“ECHO OFF”命令行自身的显示，则需要在该命令行前加上“@”。
（2）显示当前ECHO设置状态
格式:echo
（3）输出提示信息
格式：ECHO 信息内容
上述是ECHO命令常见的三种用法，也是大家熟悉和会用的，但作为DOS命令淘金者你还应该知道下面的技巧：
（4）关闭DOS命令提示符
在DOS提示符状态下键入ECHO OFF，能够关闭DOS提示符的显示使屏幕只留下光标，直至键入ECHO ON，提示符才会重新出现。
（5）输出空行，即相当于输入一个回车
格式：ECHO．
值得注意的是命令行中的“．”要紧跟在ECHO后面中间不能有空格，否则“．”将被当作提示信息输出到屏幕。另外“．”可以用，：；”／[\]＋等任一符号替代。
命令ECHO．输出的回车，经DOS管道转向可以作为其它命令的输入，比如echo.|time即相当于在TIME命令执行后给出一个回车。所以执行时系统会在显示当前时间后，自动返回到DOS提示符状态
（6）答复命令中的提问
格式：ECHO 答复语|命令文件名
上述格式可以用于简化一些需要人机对话的命令（如：CHKDSK／F；FORMAT Drive:；del *.*）的操作，它是通过DOS管道命令把ECHO命令输出的预置答复语作为人机对话命令的输入。下面的例子就相当于在调用的命令出现人机对话时输入“Y”回车：
C:>ECHO Y|CHKDSK/F
C:>ECHO Y|DEL A :*.*
（7）建立新文件或增加文件内容
格式：ECHO 文件内容>文件名
ECHO 文件内容>>文件名

例如：

> C:>ECHO @ECHO OFF>AUTOEXEC.BAT建立自动批处理文件
> C:>ECHO C:\CPAV\BOOTSAFE>>AUTOEXEC.BAT向自动批处理文件中追加内容
> C:>TYPE AUTOEXEC.BAT显示该自动批处理文件
> @ECHO OFF
> C:\CPAV\BOOTSAFE

（8）向打印机输出打印内容或打印控制码
格式：ECHO 打印机控制码>;PRN
ECHO 打印内容>;PRN

下面的例子是向M－1724打印机输入打印控制码。＜Alt＞156是按住Alt键在小键盘键入156，类似情况依此类推：

C:>ECHO +156+42+116>;PRN（输入下划线命令FS＊t）
C:>ECHO [email=+155@]+155@>;PRN[/email]（输入初始化命令ESC@）
C:>ECHO.>;PRN（换行）
（9）使喇叭鸣响
C:>ECHO ^G
“^G”是在dos窗口中用Ctrl＋G或Alt＋007输入，输入多个^G可以产生多声鸣响。使用方法是直接将其加入批处理文件中或做成批处理文件调用。
这里的“^G”属于特殊符号的使用，请看本文后面的章节

**3、PAUSE**

PAUSE，玩游戏的人都知道，暂停的意思
在这里就是停止系统命令的执行并显示下面的内容。
例：

PAUSE

运行显示：
请按任意键继续. . .
要显示其他提示语，可以这样用：
Echo 其他提示语 & pause > nul

**4、errorlevel**

程序返回码
echo %errorlevel%
每个命令运行结束，可以用这个命令行格式查看返回码
用于判断刚才的命令是否执行成功
默认值为0，一般命令执行出错会设 errorlevel 为1

**5、title**

设置cmd窗口的标题
title 新标题 #可以看到cmd窗口的标题栏变了

**6、COLOR**

设置默认的控制台前景和背景颜色。
COLOR [attr]
attr 指定控制台输出的颜色属性
颜色属性由两个十六进制数字指定 -- 第一个为背景，第二个则为
前景。每个数字可以为以下任何值之一:
0 = 黑色 8 = 灰色
1 = 蓝色 9 = 淡蓝色
2 = 绿色 A = 淡绿色
3 = 湖蓝色 B = 淡浅绿色
4 = 红色 C = 淡红色
5 = 紫色 D = 淡紫色
6 = 黄色 E = 淡黄色
7 = 白色 F = 亮白色
如果没有给定任何参数，该命令会将颜色还原到 CMD.EXE 启动时
的颜色。这个值来自当前控制台窗口、/T 开关或
DefaultColor 注册表值。
如果用相同的前景和背景颜色来执行 COLOR 命令，COLOR 命令
会将 ERRORLEVEL 设置为 1。
例如: "COLOR fc" 在亮白色上产生亮红色

**7、mode 配置系统设备**

配置系统设备。
串行口:　　　 MODE COMm[:] [BAUD=b] [PARITY=p] [DATA=d] [STOP=s]
[to=on|off] [xon=on|off] [odsr=on|off]
[octs=on|off] [dtr=on|off|hs]
[rts=on|off|hs|tg] [idsr=on|off]
设备状态: MODE [device] [/STATUS]
打印重定向:　　 MODE LPTn[:]=COMm[:]
选定代码页:　　 MODE CON[:] CP SELECT=yyy
代码页状态:　　 MODE CON[:] CP [/STATUS]
显示模式:　　 MODE CON[:] [COLS=c] [LINES=n]
击键率:　 MODE CON[:] [RATE=r DELAY=d]
例：
mode con cols=113 lines=15 & color 9f
此命令设置DOS窗口大小：15行，113列

**8、GOTO 和 :**

GOTO会点编程的朋友就会知道这是跳转的意思。
在批处理中允许以“:XXX”来构建一个标号，然后用GOTO XXX跳转到标号:XXX处，然后执行标号后的命令。
例：

> if {%1}=={} goto noparms
> if "%2"=="" goto noparms

标签的名字可以随便起，但是最好是有意义的字符串啦，前加个冒号用来表示这个字符串是标签，goto命令就是根据这个冒号（:）来寻找下一步跳到到那里。最好有一些说明这样你别人看起来才会理解你的意图啊。

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``:start``set` `/a var+=1``echo` `%var%``if %var% leq 3 GOTO start``pause`
```

运行显示：

> 1
> 2
> 3
> 4

**9、find**

在文件中搜索字符串。
FIND [/V] [/C] [/N] [/I] [/OFF[LINE]] "string" [[drive:][path]filename[ ...]]
/V 显示所有未包含指定字符串的行。
/C 仅显示包含字符串的行数。
/N 显示行号。
/I 搜索字符串时忽略大小写。
/OFF[LINE] 不要跳过具有脱机属性集的文件。
"string" 指定要搜索的文字串，
[drive:][path]filename
指定要搜索的文件。
如果没有指定路径，FIND 将搜索键入的或者由另一命令产生的文字。
Find常和type命令结合使用

Type [drive:][path]filename | find "string" [>tmpfile] #挑选包含string的行
Type [drive:][path]filename | find /v "string" #剔除文件中包含string的行
Type [drive:][path]filename | find /c #显示文件行数

以上用法将去除find命令自带的提示语（文件名提示）

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `111 >test.txt``echo` `222 >>test.txt``find ``"111"` `test.txt``del` `test.txt``pause`
```

运行显示如下：

---------- TEST.TXT
111

请按任意键继续. . .

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `111 >test.txt``echo` `222 >>test.txt``type` `test.txt|find ``"111"``del` `test.txt``pause`
```

运行显示如下：

111

请按任意键继续. . .

**10、start 命令**

批处理中调用外部程序的命令（该外部程序在新窗口中运行，批处理程序继续往下执行，不理会外部程序的运行状况），如果直接运行外部程序则必须等外部程序完成后才继续执行剩下的指令

例：start explorer d:\

调用图形界面打开D盘

**11、assoc 和 ftype**

文件关联
assoc 设置'文件扩展名'关联，关联到'文件类型'
ftype 设置'文件类型'关联，关联到'执行程序和参数'
当你双击一个.txt文件时，windows并不是根据.txt直接判断用 notepad.exe 打开
而是先判断.txt属于 txtfile '文件类型'
再调用 txtfile 关联的命令行 txtfile=%SystemRoot%\system32\NOTEPAD.EXE %1
可以在"文件夹选项"→"文件类型"里修改这2种关联
assoc #显示所有'文件扩展名'关联
assoc .txt #显示.txt代表的'文件类型'，结果显示 .txt=txtfile
assoc .doc #显示.doc代表的'文件类型'，结果显示 .doc=Word.Document.8
assoc .exe #显示.exe代表的'文件类型'，结果显示 .exe=exefile
ftype #显示所有'文件类型'关联
ftype exefile #显示exefile类型关联的命令行，结果显示 exefile="%1" %*
assoc .txt=Word.Document.8
设置.txt为word类型的文档，可以看到.txt文件的图标都变了
assoc .txt=txtfile

恢复.txt的正确关联

ftype exefile="%1" %*

恢复 exefile 的正确关联
如果该关联已经被破坏，可以运行 command.com ，再输入这条命令

**12、pushd 和 popd**

切换当前目录

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``c: & ``cd``\ & md mp3 ``#在 C:\ 建立 mp3 文件夹``md d:\mp4 ``#在 D:\ 建立 mp4 文件夹``cd` `/d d:\mp4 ``#更改当前目录为 d:\mp4``pushd` `c:\mp3 ``#保存当前目录，并切换当前目录为 c:\mp3``popd` `#恢复当前目录为刚才保存的 d:\mp4`
```

一般用处不大，在当前目录名不确定时，会有点帮助。（dos编程中很有用）

**13、CALL**

CALL命令可以在批处理执行过程中调用另一个批处理，当另一个批处理执行完后，再继续执行原来的批处理
CALL command
调用一条批处理命令，和直接执行命令效果一样，特殊情况下很有用，比如变量的多级嵌套，见教程后面。在批处理编程中，可以根据一定条件生成命令字符串，用call可以执行该字符串，见例子。
CALL [drive:][path]filename [batch-parameters]
调用的其它批处理程序。filename 参数必须具有 .bat 或 .cmd 扩展名。
CALL :label arguments
调用本文件内命令段，相当于子程序。被调用的命令段以标签:label开头
以命令goto :eof结尾。
另外，批脚本文本参数参照(%0、%1、等等)已如下改变:
批脚本里的 %* 指出所有的参数(如 %1 %2 %3 %4 %5 ...)
批参数(%n)的替代已被增强。您可以使用以下语法:（看不明白的直接运行后面的例子）
%~1 - 删除引号(")，扩充 %1
%~f1 - 将 %1 扩充到一个完全合格的路径名
%~d1 - 仅将 %1 扩充到一个驱动器号
%~p1 - 仅将 %1 扩充到一个路径
%~n1 - 仅将 %1 扩充到一个文件名
%~x1 - 仅将 %1 扩充到一个文件扩展名
%~s1 - 扩充的路径指含有短名
%~a1 - 将 %1 扩充到文件属性
%~t1 - 将 %1 扩充到文件的日期/时间
%~z1 - 将 %1 扩充到文件的大小
%~PATH:1−查找列在PATH环境变量的目录，并将PATH:1 - 在列在 PATH 环境变量中的目录里查找 %1，
并扩展到找到的第一个文件的驱动器号和路径。
%~ftza1 - 将 %1 扩展到类似 DIR 的输出行。
在上面的例子中，%1 和 PATH 可以被其他有效数值替换。
%~ 语法被一个有效参数号码终止。%~ 修定符不能跟 %*使用
注意：参数扩充时不理会参数所代表的文件是否真实存在，均以当前目录进行扩展
要理解上面的知识，下面的例子很关键。

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``Echo` `产生一个临时文件 > tmp.txt``Rem 下行先保存当前目录，再将c:\windows设为当前目录``pushd` `c:\windows``Call :sub tmp.txt``Rem 下行恢复前次的当前目录``Popd``Call :sub tmp.txt``pause``Del` `tmp.txt``exit``:sub``Echo` `删除引号： %~1``Echo` `扩充到路径： %~f1``Echo` `扩充到一个驱动器号： %~d1``Echo` `扩充到一个路径： %~p1 ``Echo` `扩充到一个文件名： %~n1``Echo` `扩充到一个文件扩展名： %~x1``Echo` `扩充的路径指含有短名： %~s1 ``Echo` `扩充到文件属性： %~a1 ``Echo` `扩充到文件的日期/时间： %~t1 ``Echo` `扩充到文件的大小： %~z1 ``Echo` `扩展到驱动器号和路径：%~dp1``Echo` `扩展到文件名和扩展名：%~nx1``Echo` `扩展到类似 ``DIR` `的输出行：%~ftza1``Echo``.``Goto :eof`
```

例：

> set aa=123456
> set cmdstr=echo %aa%
> call %cmdstr%
> pause

本例中如果不用call，而直接运行%cmdstr%，将显示结果%aa%，而不是123456

**14、shift**

更改批处理文件中可替换参数的位置。
SHIFT [/n]
如果命令扩展名被启用，SHIFT 命令支持/n 命令行开关；该命令行开关告诉
命令从第 n 个参数开始移位；n 介于零和八之间。例如:
SHIFT /2
会将 %3 移位到 %2，将 %4 移位到 %3，等等；并且不影响 %0 和 %1。

**15、IF**

IF 条件判断语句，语法格式如下：
IF [NOT] ERRORLEVEL number command
IF [NOT] string1==string2 command
IF [NOT] EXIST filename command
下面逐一介绍，更详细的分析请看后面章节。

(1) IF [NOT] ERRORLEVEL number command
IF ERRORLEVEL这个句子必须放在某一个命令的后面，执行命令后由IF ERRORLEVEL 来判断命令的返回值。
Number的数字取值范围0~255，判断时值的排列顺序应该由大到小。返回的值大于等于指定的值时，条件成立
例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``dir` `c:``rem退出代码为>=1就跳至标题1处执行，>=0就跳至标题0处执行``IF ERRORLEVEL 1 goto 1``IF ERRORLEVEL 0 goto 0``Rem 上面的两行不可交换位置，否则失败了也显示成功。``:0``echo` `命令执行成功！``Rem 程序执行完毕跳至标题exit处退出``goto exit``:1``echo` `命令执行失败！``Rem 程序执行完毕跳至标题exit处退出``goto exit``:exit``pause`
```

运行显示：命令执行成功！

(2) IF [NOT] string1==string2 command
string1和string2都为字符的数据，英文内字符的大小写将看作不同，这个条件中的等于号必须是两个（绝对相等的意思）
条件相等后即执行后面的command
检测当前变量的值做出判断，为了防止字符串中含有空格，可用以下格式
if [NOT] {string1}=={string2} command
if [NOT] [string1]==[string2] command
if [NOT] "string1"=="string2" command
这种写法实际上将括号或引号当成字符串的一部分了，只要等号左右两边一致就行了，比如下面的写法就不行：
if {string1}==[string2] command

(3) IF [NOT] EXIST filename command
EXIST filename为文件或目录存在的意思
echo off
IF EXIST autoexec.bat echo 文件存在！
IF not EXIST autoexec.bat echo 文件不存在！
这个批处理大家可以放在C盘和D盘分别执行，看看效果

**16、setlocal 与 变量延迟**

本条内容引用[英雄出品]的批处理教程：
要想进阶，变量延迟是必过的一关！所以这一部分希望你能认真看。
为了更好的说明问题，我们先引入一个例子。

例1:

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``set` `a=4``set` `a=5 & ``echo` `%a%``pause`
```

结果：4

解说：为什么是4而不是5呢？在echo之前明明已经把变量a的值改成5了？
让我们先了解一下批处理运行命令的机制：
批 处理读取命令时是按行读取的（另外例如for命令等，其后用一对圆括号闭合的所有语句也当作一行），在处理之前要完成必要的预处理工作，这其中就包括对该 行命令中的变量赋值。我们现在分析一下例1，批处理在运行到这句“set a=5 & echo %a%”之前，先把这一句整句读取并做了预处理——对变量a赋了值，那么%a%当然就是4了！（没有为什么，批处理就是这样做的。）
而为了能够感知环境变量的动态变化，批处理设计了变量延迟。简单来说，在读取了一条完整的语句之后，不立即对该行的变量赋值，而会在某个单条语句执行之前再进行赋值，也就是说“延迟”了对变量的赋值。
那么如何开启变量延迟呢？变量延迟又需要注意什么呢？举个例子说明一下：

例2:

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``setlocal enabledelayedexpansion``set` `a=4``set` `a=5 & ``echo` `!a!``pause`
```

结果：5

解说：启动了变量延迟，得到了正确答案。变量延迟的启动语句是“setlocal enabledelayedexpansion”，并且变量要用一对叹号“!!”括起来（注意要用英文的叹号），否则就没有变量延迟的效果。
分析一下例2，首先“setlocal enabledelayedexpansion”开启变量延迟，然后“set a=4”先给变量a赋值为
4，“set a=5 & echo !a!”这句是给变量a赋值为5并输出（由于启动了变量延迟，所以批处理能够感知到动态变化，即不是先给该行变量赋值，而是在运行过程中给变量赋值，因此此时a的值就是5了）。
再举一个例子巩固一下。

例3:

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``setlocal enabledelayedexpansion``for /l %%i in (1,1,5) do (``set` `a=%%i``echo` `!a!``)``pause`
```

结果：

1
2
3
4
5

解说：本例开启了变量延迟并用“!!”将变量扩起来，因此得到我们预期的结果。如果不用变量延迟会出现什
么结果呢？结果是这样的：
ECHO 处于关闭状态。
ECHO 处于关闭状态。
ECHO 处于关闭状态。
ECHO 处于关闭状态。
ECHO 处于关闭状态。
即没有感知到for语句中的动态变化。
提示：在没有开启变量延迟的情况下，某条命令行中的变量改变，必须到下一条命令才能体现。这一点也可以加以利用，看例子。
例：交换两个变量的值，且不用中间变量

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``::目的：交换两个变量的值，但是不使用临时变量``::Code by JM 2007-1-24 [email=CMD@XP]CMD@XP[/email]``::出处：http://www.cn``-dos``.net/forum/viewthread.php``?``tid=27078``set` `var1=abc``set` `var2=123``echo` `交换前： var1=%var1% var2=%var2%``set` `var1=%var2%& ``set` `var2=%var1%``echo` `交换后： var1=%var1% var2=%var2%``pause`
```

**17、ATTRIB 显示或更改文件属性**

ATTRIB [+R|-R] [+A|-A] [+S|-S] [+H|-H] [[drive:] [path] filename] [/S [/D]]
\+ 设置属性。
\- 清除属性。
R 只读文件属性。
A 存档文件属性。
S 系统文件属性。
H 隐藏文件属性。
[drive:][path][filename]
指定要处理的文件属性。
/S 处理当前文件夹及其子文件夹中的匹配文件。
/D 也处理文件夹。

例：

> md autorun
> attrib +a +s +h autorun

上面的命令将建立文件夹autorun，然后将其设为存档、系统、隐藏属性

## 第二节 常用特殊符号

1、@ 命令行回显屏蔽符
2、% 批处理变量引导符
3、> 重定向符
4、>> 重定向符
5、<、>&、<& 重定向符
6、| 命令管道符
7、^ 转义字符
8、& 组合命令
9、&& 组合命令
10、|| 组合命令
11、"" 字符串界定符
12、, 逗号
13、; 分号
14、() 括号
15、! 感叹号
16、批处理中可能会见到的其它特殊标记符: （略）
CR(0D) 命令行结束符
Escape(1B) ANSI转义字符引导符
Space(20) 常用的参数界定符
Tab(09) ; = 不常用的参数界定符
\+ COPY命令文件连接符
\* ? 文件通配符
/ 参数开关引导符
: 批处理标签引导符

废话少说，开讲了

**1、@ 命令行回显屏蔽符**

这个字符在批处理中的意思是关闭当前行的回显。我们从前几课知道
ECHO OFF可以关闭掉整个批处理命令的回显，但不能关掉ECHO OFF这个命令，现在我们在ECHO OFF这个命令前加个@，就可以达到所有命令均不回显的要求

**2、% 批处理变量引导符**

这个百分号严格来说是算不上命令的，它只是批处理中的参数而已（多个%一起使用的情况除外，以后还将详细介绍）。
引用变量用%var%，调用程序外部参数用%1至%9等等
%0 %1 %2 %3 %4 %5 %6 %7 %8 %9 %*为命令行传递给批处理的参数
%0 批处理文件本身，包括完整的路径和扩展名
%1 第一个参数
%9 第九个参数
%* 从第一个参数开始的所有参数
参数%0具有特殊的功能，可以调用批处理自身，以达到批处理本身循环的目的，也可以复制文件自身等等。
例：最简单的复制文件自身的方法
copy %0 d:\wind.bat
小技巧：添加行内注释
%注释内容%（可以用作行内注释，不能出现重定向符号和管道符号）
为什么这样呢？此时“注释内容”其实被当作变量，其值是空的，故只起注释作用，不过这种用法容易出现语法错误，一般不用。

**3、> 重定向符**

输出重定向命令
DOS的标准输入输出通常是在标准设备键盘和显示器上进行的，利用重定向,可以方便地将输入输出改向磁盘文件或其它设备。其中:
1.大于号“>”将命令发送到文件或设备，例如打印机>prn。使用大于号“>”时，有些命令输出(例如错误消息)不能重定向。
2.双大于号“>>”将命令输出添加到文件结尾而不删除文件中已有的信息。
3.小于号“<”从文件而不是键盘上获取命令所需的输入。
4.>&符号将输出从一个默认I/O流(stdout,stdin,stderr)重新定向到另一个默认I/O流。
例如，command >output_file 2>&1将处理command过程中的所有错误信息从屏幕重定向到标准文件输出中。标准输出的数值如下所示：

命令重定向的标准句柄



| 句柄名称  | 值   | 说明                              |
| --------- | ---- | --------------------------------- |
| STDIN     | 0    | 标准输入，发送自键盘              |
| STDUOT    | 1    | 标准输出，发送到命令Shell窗口     |
| STDERR    | 2    | 标准错误输出，发送到命令Shell窗口 |
| UNDEFINED | 3~9  | 特定于应用程序的句柄              |



这个字符的意思是传递并且覆盖，他所起的作用是将运行的结果传递到后面的范围（后边可以是文件，也可以是默认的系统控制台）

在NT系列命令行中，重定向的作用范围由整个命令行转变为单个命令语句，受到了命令分隔符&,&&,||和语句块的制约限制。
比如：

使用命令：echo hello >1.txt将建立文件1.txt，内容为”hello “（注意行尾有一空格）
使用命令：echo hello>1.txt将建立文件1.txt，内容为”hello“（注意行尾没有空格）：

具体重定向实例请看这篇文章：[DOS的重定向命令及在安全方面的应用](https://www.jb51.net/article/151916.htm)

**4、>> 重定向符**

输出重定向命令
这个符号的作用和>有点类似，但他们的区别是>>是传递并在文件的末尾追加，而>是覆盖
用法同上
同样拿1.txt做例子
使用命令：
echo hello > 1.txt
echo world >>1.txt
这时候1.txt 内容如下:
hello
world

**5、<、>&、<& 重定向符**

这三个命令也是管道命令，但它们一般不常用，你只需要知道一下就ok了，当然如果想仔细研究的话，可以自己查一下资料。(本人已查过，网上也查不到相关资料)
<，输入重定向命令，从文件中读入命令输入，而不是从键盘中读入。
@echo off
echo 2005-05-01>temp.txt
date <temp.txt
del temp.txt
这样就可以不等待输入直接修改当前日期
\>&，将一个句柄的输出写入到另一个句柄的输入中。
<&，刚好和>&相反，从一个句柄读取输入并将其写入到另一个句柄输出中。
常用句柄：0、1、2，未定义句柄：3—9
1>nul 表示禁止输出正确的信息
2>nul 表示禁止输出错误信息。
其中的1与2都是代表某个数据流输入输出的地址（NT CMD 称之为句柄，MSDOS称之为设备）。
句柄0：标准输入stdin，键盘输入
句柄1：标准输出stdout，输出到命令提示符窗口（console，代码为CON）
句柄2：标准错误stderr，输出到命令提示符窗口（console，代码为CON）
其中的stdin可被<重定向，stdout可被>、>>重定向。
我们已经知道读取文本中的内容可以用for命令，但如果只需要读取第一行用for命令就有点麻烦。简单的办法如下:
@echo off
set /p str=<%0
echo %str%
pause
运行显示批处理文件自身的第一行：@echo off

**6、| 命令管道符**

格式：第一条命令 | 第二条命令 [| 第三条命令...]
将第一条命令的结果作为第二条命令的参数来使用，记得在unix中这种方式很常见。
例如：
dir c:\|find "txt"
以上命令是：查找C：\所有，并发现TXT字符串。
FIND的功能请用 FIND /? 自行查看
在不使format的自动格式化参数时，我是这样来自动格式化A盘的
echo y|format a: /s /q /v:system
用过format的都知道，再格盘时要输入y来确认是否格盘，这个命令前加上echo y并用|字符来将echo y的结果传给format命令
从而达到自动输入y的目的
（这条命令有危害性，测试时请慎重）

**7、^ 转义字符**

^是对特殊符号<,>,&的前导字符，在命令中他将以上3个符号的特殊功能去掉，仅仅只把他们当成符号而不使用他们的特殊意义。
比如
echo test ^>1.txt
结果则是：test > 1.txt
他没有追加在1.txt里，呵呵。只是显示了出来
另外，此转义字符还可以用作续行符号。
举个简单的例子：

> @echo off
> echo 英雄^
> 是^
> 好^
> 男人
> pause

不用多说，自己试一下就明白了。
为什么转义字符放在行尾可以起到续行符的作用呢？原因很简单，因为每行末尾还有一个看不见的符号，即回车符，转义字符位于行尾时就让回车符失效了，从而起到了续行的作用。

**8、& 组合命令**

语法：第一条命令 & 第二条命令 [& 第三条命令...]
&、&&、||为组合命令，顾名思义，就是可以把多个命令组合起来当一个命令来执行。这在批处理脚本里是允许的，而且用的非常广泛。因为批处理认行不认命令数目。
这个符号允许在一行中使用2个以上不同的命令，当第一个命令执行失败了，也不影响后边的命令执行。
这里&两边的命令是顺序执行的，从前往后执行。
比如：
dir z:\ & dir y:\ & dir c:\
以上命令会连续显示z,y,c盘的内容，不理会该盘是否存在

**9、&& 组合命令**

语法：第一条命令 && 第二条命令 [&& 第三条命令...]
用这种方法可以同时执行多条命令，当碰到执行出错的命令后将不执行后面的命令，如果一直没有出错则一直执行完所有命令
这个命令和上边的类似，但区别是，第一个命令失败时，后边的命令也不会执行
dir z:\ && dir y:\ && dir c:\

**10、|| 组合命令**

语法：第一条命令 || 第二条命令 [|| 第三条命令...]
用这种方法可以同时执行多条命令，当一条命令失败后才执行第二条命令，当碰到执行正确的命令后将不执行后面的命令，如果没有出现正确的命令则一直执行完所有命令；

提示：组合命令和重定向命令一起使用必须注意优先级
管道命令的优先级高于重定向命令，重定向命令的优先级高于组合命令
问题：把C盘和D盘的文件和文件夹列出到a.txt文件中。看例：
dir c:\ && dir d:\ > a.txt
这 样执行后a.txt里只有D盘的信息！为什么？因为组合命令的优先级没有重定向命令的优先级高！所以这句在执行时将本行分成这两部分：dir c:\和dir d:\ > a.txt，而并不是如你想的这两部分：dir c:\ && dir d:\和> a.txt。要使用组合命令&&达到题目的要求，必须得这么写：
dir c:\ > a.txt && dir d:\ >> a.txt
这样，依据优先级高低，DOS将把这句话分成以下两部分：dir c:\ > a.txt和dir d:\ >> a.txt。例十八中的几句的差别比较特殊，值得好好研究体会一下。
当然这里还可以利用&命令（自己想一下道理哦）：
dir c:\ > a.txt & dir d:\ >> a.txt
[这个也可以用 dir c:\;d:\ >>a.txt 来实现]

**11、"" 字符串界定符**

双引号允许在字符串中包含空格，进入一个特殊目录可以用如下方法
cd "program files"
cd progra~1
cd pro*
以上三种方法都可以进入program files这个目录

**12、, 逗号**

逗号相当于空格，在某些情况下“,”可以用来当做空格使
比如
dir,c:\

**13、; 分号**

分号，当命令相同时，可以将不同目标用；来隔离，但执行效果不变，如执行过程中发生错误，则只返回错误报告，但程序仍会执行。（有人说不会继续执行，其实测试一下就知道了，只不过它的执行有个规则，请看下面的规则）
比如：
dir c:\;d:\;e:\;z:\
以上命令相当于
dir c:\
dir d:\
dir e:\
dir f:\
如果其中z盘不存在，运行显示：系统找不到指定的路径。然后终止命令的执行。
例：dir c:\;d:\;e:\1.txt
以上命令相当于
dir c:\
dir d:\
dir e:\1.txt
其中文件e:\1.txt不存在，但e盘存在，有错误提示，但命令仍会执行。

规则：(我是在操作系统是XP SP3,英文版下测试的)
1.如果目标路径不存在，则整个语句都不执行，例如dir c:\;c:\dfdfdf\a.txt，则根本不会执行，因为我没有c:\dfdfdf\这个目录；
2.如果路径存在，仅文件不存在，则会继续执行，并且提示文件不存在的错误，例如：dir c:\;c:\temp\a.txt，我的目录中有c:\temp\文件夹，但这个目录下面没有1.txt这个文件。
就说这些了!各位有什么意见请回贴!有什么疑问请到BAT交流区发贴!下一节改进!

**14、() 括号**

小括号在批处理编程中有特殊的作用，左右括号必须成对使用，括号中可以包括多行命令，这些命令将被看成一个整体，视为一条命令行。
括号在for语句和if语句中常见，用来嵌套使用循环或条件语句，其实括号()也可以单独使用，请看例子。
例：
命令：echo 1 & echo 2 & echo 3
可以写成：
(
echo 1
echo 2
echo 3
)
上面两种写法效果一样，这两种写法都被视为是一条命令行。
注意：这种多条命令被视为一条命令行时，如果其中有变量，就涉及到变量延迟的问题。

**15、! 感叹号**

没啥说的，在变量延迟问题中，用来表示变量，即%var%应该表示为!var!，请看前面的setlocal命令介绍。

**第二章 DOS循环：for命令详解**

讲FOR之前呢,咋先告诉各位新手朋友,如果你有什么命令不懂,直接在CMD下面输入:
name /? 这样的格式来看系统给出的帮助文件,比如for /? 就会把FOR命令的帮助全部显示出来!当然许多菜鸟都看不懂....所以才会有那么多批处理文章!!!!俺也照顾菜鸟,把FOR命令用我自己的方式说明下!
正式开始:

**一、基本格式**

FOR %%variable IN (set) DO command [command-parameters]
%%variable 指定一个单一字母表示可替换的参数。
(set) 指定一个或一组文件。可以使用通配符。
command 指定对每个文件执行的命令。
command-parameters
为特定命令指定参数或命令行开关。



参数:FOR有4个参数 /d /l /r /f 他们的作用我在下面用例子解释
现在开始讲每个参数的意思

**二、参数 /d**

FOR /D %%variable IN (set) DO command [command-parameters]
如果集中包含通配符，则指定与目录名匹配，而不与文件
名匹配。
如果 Set (也就是我上面写的 "相关文件或命令") 包含通配符（* 和 ?），将对与 Set 相匹配的每个目录（而不是指定目录中的文件组）执行指定的 Command。
这个参数主要用于目录搜索,不会搜索文件,看这样的例子

> @echo off
> for /d %%i in (c:\*) do echo %%i
> pause

运行会把C盘根目录下的全部目录名字打印出来,而文件名字一个也不显示!
在来一个,比如我们要把当前路径下文件夹的名字只有1-3个字母的打出来

> @echo off
> for /d %%i in (???) do echo %%i
> pause

这样的话如果你当前目录下有目录名字只有1-3个字母的,就会显示出来,没有就不显示了
这里解释下*号和?号的作用,*号表示任意N个字符,而?号只表示任意一个字符
知道作用了,给大家个思考题目!

> @echo off
> for /d %%i in (window?) do echo %%i
> pause

保存到C盘下执行,会显示什么呢?自己看吧! 显示：windows
/D参数只能显示当前目录下的目录名字,这个大家要注意!

**三、参数 /R**

FOR /R [[drive:]path] %%variable IN (set) DO command [command-parameters]
检查以 [drive:]path 为根的目录树，指向每个目录中的
FOR 语句。如果在 /R 后没有指定目录，则使用当前
目录。如果集仅为一个单点(.)字符，则枚举该目录树。

**递归**

上面我们知道,/D只能显示当前路径下的目录名字,那么现在这个/R也是和目录有关,他能干嘛呢?放心他比/D强大多了!
他可以把当前或者你指定路径下的文件名字全部读取,注意是文件名字,有什么用看例子!
请注意2点：
1、set中的文件名如果含有通配符(？或*)，则列举/R参数指定的目录及其下面的所用子目录中与set相符合的所有文件，无相符文件的目录则不列举。
2、相反，如果set中为具体文件名，不含通配符，则枚举该目录树（即列举该目录及其下面的所有子目录），而不管set中的指定文件是否存在。这与前面所说的单点（.）枚举目录树是一个道理，单点代表当前目录，也可视为一个文件。
例：

> @echo off
> for /r c:\ %%i in (*.exe) do echo %%i
> pause

咱们把这个BAT保存到D盘随便哪里然后执行,我会就会看到,他把C盘根目录,和每个目录的子目录下面全部的EXE文件都列出来了!!!!
例：

> @echo off
> for /r %%i in (*.exe) do @echo %%i
> pause

参数不一样了吧!这个命令前面没加那个C:\也就是搜索路径,这样他就会以当前目录为搜索路径,比如你这个BAT你把他放在d:\test目录下执行,那么他就会把D:\test目录和他下面的子目录的全部EXE文件列出来!!!
例：

> @echo off
> for /r c:\ %%i in (boot.ini) do echo %%i
> pause

运行本例发现枚举了c盘所有目录，为了只列举boot.ini存在的目录，可改成下面这样：

> @echo off
> for /r c:\ %%i in (boot.ini) do if exist %%i echo %%i
> pause

用这条命令搜索文件真不错。。。。。。
这个参数大家应该理解了吧!还是满好玩的命令!

**四、参数 /L**

FOR /L %%variable IN (start,step,end) DO command [command-parameters]
该集表示以增量形式从开始到结束的一个数字序列。
因此，(1,1,5) 将产生序列 1 2 3 4 5，(5,-1,1) 将产生
序列 (5 4 3 2 1)。
使 用迭代变量设置起始值 (Start#)，然后逐步执行一组范围的值，直到该值超过所设置的终止值 (End#)。/L 将通过对 Start# 与 End# 进行比较来执行迭代变量。如果 Start# 小于 End#，就会执行该命令。如果迭代变量超过 End#，则命令解释程序退出此循环。还可以使用负的 Step# 以递减数值的方式逐步执行此范围内的值。例如，(1,1,5) 生成序列 1 2 3 4 5，而 (5,-1,1) 则生成序列 (5 4 3 2 1)。语法是：
看着这说明有点晕吧!咱们看例子就不晕了!

> @echo off
> for /l %%i in (1,1,5) do @echo %%i
> pause

保存执行看效果,他会打印从1 2 3 4 5 这样5个数字
(1,1,5)这个参数也就是表示从1开始每次加1直到5终止!
等会晕,就打印个数字有P用...好的满足大家,看这个例子

> @echo off
> for /l %%i in (1,1,5) do start cmd
> pause

执行后是不是吓了一跳,怎么多了5个CMD窗口,呵呵!如果把那个 (1,1,5)改成 (1,1,65535)会有什么结果,我先告诉大家,会打开65535个CMD窗口....这么多你不死机算你强!
当然我们也可以把那个start cmd改成md %%i 这样就会建立指定个目录了!!!名字为1-65535
看完这个被我赋予破坏性质的参数后,我们来看最后一个参数

**五、参数 /F**

\迭代及文件解析
使用文件解析来处理命令输出、字符串及文件内容。使用迭代变量定义要检查的内容或字符串，并使用各种options选项进一步修改解析方式。使用options令牌选项指定哪些令牌应该作为迭代变量传递。请注意：在没有使用令牌选项时，/F 将只检查第一个令牌。
文件解析过程包括读取输出、字符串或文件内容，将其分成独立的文本行以及再将每行解析成零个或更多个令牌。然后通过设置为令牌的迭代变量值，调用 for 循环。默认情况下，/F 传递每个文件每一行的第一个空白分隔符号。跳过空行。

详细的帮助格式为：

> FOR /F ["options"] %%variable IN (file-set) DO command [command-parameters]
> FOR /F ["options"] %%variable IN ("string") DO command [command-parameters]
> FOR /F ["options"] %%variable IN ('command') DO command [command-parameters]

带引号的字符串"options"包括一个或多个
指定不同解析选项的关键字。这些关键字为:
eol=c - 指一个行注释字符的结尾(就一个)(备注：默认以使用；号为行首字符的为注释行)
skip=n - 指在文件开始时忽略的行数，(备注：最小为1，n可以大于文件的总行数，默认为1。)
delims=xxx - 指分隔符集。这个替换了空格和跳格键的默认分隔符集。
tokens=x,y,m-n - 指每行的哪一个符号被传递到每个迭代
的 for 本身。这会导致额外变量名称的分配。m-n
格式为一个范围。通过 nth 符号指定 mth。如果
符号字符串中的最后一个字符星号，
那么额外的变量将在最后一个符号解析之后
分配并接受行的保留文本。经测试，该参数最多
只能区分31个字段。(备注：默认为1，则表示只显示分割后的第一列的内容，最大是31，超过最大则无法表示)
usebackq - 使用后引号（键盘上数字1左面的那个键`）。
未使用参数usebackq时：file-set表示文件，但不能含有空格
双引号表示字符串，即"string"
单引号表示执行命令，即'command'
使用参数usebackq时：file-set和"file-set"都表示文件
当文件路径或名称中有空格时，就可以用双引号括起来
单引号表示字符串，即'string'
后引号表示命令执行，即`command`

以上是用for /?命令获得的帮助信息，直接复制过来的，括号中的备注为我添加的说明。
晕惨了!我这就举个例子帮助大家来理解这些参数!

For命令例1：****************************************

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``rem 首先建立临时文件test.txt``echo` `;注释行,这是临时文件,用完删除 >test.txt``echo` `11段 12段 13段 14段 15段 16段 >>test.txt``echo` `21段,22段,23段,24段,25段,26段 >>test.txt``echo` `31段-32段-33段-34段-35段-36段 >>test.txt``FOR /F ``"eol=; tokens=1,3* delims=,- "` `%%i in (test.txt) do ``echo` `%%i %%j %%k``Pause``Del` `test.txt`
```

运行显示结果：

11段 13段 14段 15段 16段
21段 23段 24段,25段,26段
31段 33段 34段-35段-36段
请按任意键继续. . .

为什么会这样?我来解释：
eol=; 分号开头的行为注释行
tokens=1,3* 将每行第1段,第3段和剩余字段分别赋予变量%%i，%%j，%%k
delims=,- （减号后有一空格）以逗号减号和空格为分隔符，空格必须放在最后

For命令例2：****************************************

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``FOR /F ``"eol= delims="` `%%i in (test.txt) do ``echo` `%%i``Pause`
```

运行将显示test.txt全部内容，包括注释行，不解释了哈。

For命令例3：****************************************
另外/F参数还可以以输出命令的结果看这个例子

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``FOR /F ``"delims="` `%%i in (``'net user'``) do @``echo` `%%i``pause`
```

这样你本机全部帐号名字就出来了把扩号内的内容用两个单引号引起来就表示那个当命令执行,FOR会返回命令的每行结果,加那个"delims=" 是为了让我空格的行能整行显示出来,不加就只显示空格左边一列!

基本上讲完了FOR的基本用法了...如果你看过FOR的系统帮助,你会发现他下面还有一些特定义的变量,这些我先不讲.大家因该都累了吧!你不累我累啊....
所谓文武之道，一张一弛，现休息一下。

**第三章 FOR命令中的变量**

FOR命令中有一些变量,他们的用法许多新手朋友还不太了解,今天给大家讲解他们的用法!

先把FOR的变量全部列出来:
~I - 删除任何引号(")，扩展 %I
%~fI - 将 %I 扩展到一个完全合格的路径名
%~dI - 仅将 %I 扩展到一个驱动器号
%~pI - 仅将 %I 扩展到一个路径
%~nI - 仅将 %I 扩展到一个文件名
%~xI - 仅将 %I 扩展到一个文件扩展名
%~sI - 扩展的路径只含有短名
%~aI - 将 %I 扩展到文件的文件属性
%~tI - 将 %I 扩展到文件的日期/时间
%~zI - 将 %I 扩展到文件的大小
%~$PATH:I - 查找列在路径环境变量的目录，并将 %I 扩展
到找到的第一个完全合格的名称。如果环境变量名
未被定义，或者没有找到文件，此组合键会扩展到
空字符串

我们可以看到每行都有一个大写字母"I",这个I其实就是我们在FOR带入的变量,我们FOR语句代入的变量名是什么,这里就写什么.
比如:FOR /F %%z IN ('set') DO @echo %%z
这里我们代入的变量名是z那么我们就要把那个I改成z,例如%~fI改为%~fz
至于前面的%~p这样的内容就是语法了!

好开始讲解:

**一、 ~I - 删除任何引号(")，扩展 %I**

这个变量的作用就如他的说明,删除引号!
我们来看这个例子:
首先建立临时文件temp.txt，内容如下

> "1111
> "2222"
> 3333"
> "4444"44
> "55"55"55

可建立个BAT文件代码如下:

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `^"1111>temp.txt``echo` `"2222"``>>temp.txt``echo` `3333^">>temp.txt``echo` `"4444"``44>>temp.txt``echo` `^``"55"``55"55>>temp.txt` `rem 上面建立临时文件，注意不成对的引号要加转义字符^，重定向符号前不要留空格``FOR /F ``"delims="` `%%i IN (temp.txt) DO ``echo` `%%~i``pause``del` `temp.txt`
```

执行后,我们看CMD的回显如下:
1111 #字符串前的引号被删除了
2222 #字符串首尾的引号都被删除了
3333" #字符串前无引号，后面的引号保留
4444"44 #字符串前面的引号删除了，而中间的引号保留
55"55"55 #字符串前面的引号删除了，而中间的引号保留
请按任意键继续. . .
和之前temp.txt中的内容对比一下,我们会发现第1、2、5行的引号都消失了,这就是删除引号~i的作用了!
删除引号规则如下(BAT兄补充!)
1、若字符串首尾同时存在引号，则删除首尾的引号；
2、若字符串尾不存在引号，则删除字符串首的引号；
3、如果字符串中间存在引号，或者只在尾部存在引号，则不删除。
龙卷风补充：无头不删，有头连尾删。

**二、 %~fI - 将 %I 扩展到一个完全合格的路径名**

看例子:
把代码保存放在随便哪个地方,我这里就放桌面吧.
FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~fi
pause
执行后显示内容如下
C:\Documents and Settings\Administrator\桌面\test.bat
C:\Documents and Settings\Administrator\桌面\test.vbs
当我把代码中的 %%~fi直接改成%%i
FOR /F "delims==" %%i IN ('dir /b') DO @echo %%i
pause
执行后就会显示以下内容：
test.bat
test.vbs
通过对比,我们很容易就看出没有路径了,这就是"将 %I 扩展到一个完全合格的路径名"的作用
也就是如果%i变量的内容是一个文件名的话,他就会把这个文件所在的绝对路径打印出来,而不只单单打印一个文件名,自己动手动实验下就知道了!

**三、 %~dI - 仅将 %I 扩展到一个驱动器号**

看例子:
代码如下,我还是放到桌面执行!

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~di
> pause

执行后我CMD里显示如下
C:
C:
我桌面就两个文件test.bat,test.vbs,%%~di作用是,如果变量%%i的内容是一个文件或者目录名,他就会把他这文件
或者目录所在的盘符号打印出来!

**四、 %~pI - 仅将 %I 扩展到一个路径**

这个用法和上面一样,他只打印路径不打印文件名字

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~pi
> pause

我就不打结果了,大家自己复制代码看结果吧,下面几个都是这么个用法,代码给出来,大家自己看结果吧!

**五、 %~nI - 仅将 %I 扩展到一个文件名**

只打印文件名字

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~ni
> pause

**六、 %~xI - 仅将 %I 扩展到一个文件扩展名**

只打印文件的扩展名

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~xi
> pause

七、 %~sI - 扩展的路径只含有短名
打印绝对短文件名

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~si
> pause

**八、 %~aI - 将 %I 扩展到文件的文件属性**

打印文件的属性

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~ai
> pause

**九、 %~tI - 将 %I 扩展到文件的日期/时间**

打印文件建立的日期

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~ti
> pause

**十、 %~zI - 将 %I 扩展到文件的大小**

打印文件的大小

> FOR /F "delims==" %%i IN ('dir /b') DO @echo %%~zi
> pause

上面例子中的"delims=="可以改为"delims="，即不要分隔符

**十一、 %~$PATH:I - 查找列在路径环境变量的目录**

并将 %I 扩展到找到的第一个完全合格的名称。如果环境变量名未被定义，或者没有找到文件，此组合键会扩展到空字符串
这是最后一个,和上面那些都不一样,我单独说说!

然后在把这些代码保存为批处理,放在桌面。

> @echo off
> FOR /F "delims=" %%i IN (“notepad.exe”) DO echo %%~$PATH:i
> pause

龙卷风补充：上面代码显示结果为C:\WINDOWS\system32\notepad.exe
他的意思就在PATH变量里指定的路径里搜索notepad.exe文件，如果有notepad.exe则会把他所在绝对路径打印出来，没有就打印一个错误！

好了,FOR的的变量就介绍到这了!

**第四章 批处理中的变量**

批处理中的变量,我把他分为两类,分别为"系统变量"和"自定义变量"
我们现在来详解这两个变量!

**一、系统变量**

他们的值由系统将其根据事先定义的条件自动赋值,也就是这些变量系统已经给他们定义了值,
不需要我们来给他赋值,我们只需要调用而以! 我把他们全部列出来!

%ALLUSERSPROFILE% 本地 返回“所有用户”配置文件的位置。
%APPDATA% 本地 返回默认情况下应用程序存储数据的位置。
%CD% 本地 返回当前目录字符串。
%CMDCMDLINE% 本地 返回用来启动当前的 Cmd.exe 的准确命令行。
%CMDEXTVERSION% 系统 返回当前的“命令处理程序扩展”的版本号。
%COMPUTERNAME% 系统 返回计算机的名称。
%COMSPEC% 系统 返回命令行解释器可执行程序的准确路径。
%DATE% 系统 返回当前日期。使用与 date /t 命令相同的格式。由 Cmd.exe 生成。有关
date 命令的详细信息，请参阅 Date。
%ERRORLEVEL% 系统 返回上一条命令的错误代码。通常用非零值表示错误。
%HOMEDRIVE% 系统 返回连接到用户主目录的本地工作站驱动器号。基于主目录值而设置。用
户主目录是在“本地用户和组”中指定的。
%HOMEPATH% 系统 返回用户主目录的完整路径。基于主目录值而设置。用户主目录是在“本地用户和组”中指定的。
%HOMESHARE% 系统 返回用户的共享主目录的网络路径。基于主目录值而设置。用户主目录是
在“本地用户和组”中指定的。
%LOGONSERVER% 本地 返回验证当前登录会话的域控制器的名称。
%NUMBER_OF_PROCESSORS% 系统 指定安装在计算机上的处理器的数目。
%OS% 系统 返回操作系统名称。Windows 2000 显示其操作系统为 Windows_NT。
%PATH% 系统 指定可执行文件的搜索路径。
%PATHEXT% 系统 返回操作系统认为可执行的文件扩展名的列表。
%PROCESSOR_ARCHITECTURE% 系统 返回处理器的芯片体系结构。值：x86 或 IA64 基于
Itanium
%PROCESSOR_IDENTFIER% 系统 返回处理器说明。
%PROCESSOR_LEVEL% 系统 返回计算机上安装的处理器的型号。
%PROCESSOR_REVISION% 系统 返回处理器的版本号。
%PROMPT% 本地 返回当前解释程序的命令提示符设置。由 Cmd.exe 生成。
%RANDOM% 系统 返回 0 到 32767 之间的任意十进制数字。由 Cmd.exe 生成。
%SYSTEMDRIVE% 系统 返回包含 Windows server operating system 根目录（即系统根目录）
的驱动器。
%SYSTEMROOT% 系统 返回 Windows server operating system 根目录的位置。
%TEMP% 和 %TMP% 系统和用户 返回对当前登录用户可用的应用程序所使用的默认临时目录。
有些应用程序需要 TEMP，而其他应用程序则需要 TMP。
%TIME% 系统 返回当前时间。使用与 time /t 命令相同的格式。由 Cmd.exe 生成。有关
time 命令的详细信息，请参阅 Time。
%USERDOMAIN% 本地 返回包含用户帐户的域的名称。
%USERNAME% 本地 返回当前登录的用户的名称。
%USERPROFILE% 本地 返回当前用户的配置文件的位置。
%WINDIR% 系统 返回操作系统目录的位置。

这么多系统变量,我们如何知道他的值是什么呢?
在CMD里输入 echo %WINDIR%
这样就能显示一个变量的值了!
举个实际例子,比如我们要复制文件到当前帐号的启动目录里就可以这样
copy d:\1.bat "%USERPROFILE%\「开始」菜单\程序\启动\"
%USERNAME% 本地 返回当前登录的用户的名称。 注意有空格的目录要用引号引起来

另外还有一些系统变量,他们是代表一个意思,或者一个操作!
他们分别是%0 %1 %2 %3 %4 %5 ......一直到%9 还有一个%*
%0 这个有点特殊,有几层意思,先讲%1-%9的意思.
%1 返回批处理的第一个参数
%2 返回批处理的第二个参数
%3-%9依此推类
反回批处理参数?到底怎么个返回法?
我们看这个例子,把下面的代码保存为test.BAT然后放到C盘下

> @echo off
> echo %1 %2 %3 %4
> echo %1
> echo %2
> echo %3
> echo %4

进入CMD,输入cd c:\

然后输入 test.bat 我是第一个参数 我是第二个参数 我是第三个参数 我是第四个参数
注意中间的空格,我们会看到这样的结果:
我是第一个参数 我是第二个参数 我是第三个参数 我是第四个参数
我是第一个参数
我是第二个参数
我是第三个参数
我是第四个参数
对比下代码,%1就是”我是第一个参数” %2就是”我是第二个参数”
怎么样理解了吧!

这些%1和%9可以让批处理也能带参数运行,大大提高批处理功能!

还有一个%* 他是什么呢?他的作用不是很大,只是返回参数而已,不过他是一次返回全部参数的值,不用在输入%1 %2来确定一个个的

例子

> @echo off
> echo %*

同样保存为test.bat 放到C盘
进入CMD,输入cd c:\
然后输入 test.bat 我是第一个参数 我是第二个参数 我是第三个参数 我是第四个参数
可以看到他一次把全部参数都显示出来了

好现在开始讲那个比较特殊的%0

%0 这个不是返回参数的值了,他有两层意思!
第一层意思:返回批处理所在绝对路径
例子:

> @echo off
> echo %0
> pause

保存为test.BAT放在桌面运行,会显示如下结果
"C:\Documents and Settings\Administrator\桌面\test.bat"
他把当前批处理执行的所在路经打印出来了,这就是返回批处理所在绝对路径的意思
第二层意思:无限循环执行BAT
例子:

> @echo off
> net user
> %0

保存为BAT执行,他就会无限循环执行net user这条命令,直到你手动停止.
龙卷风补充：其实%0就是第一参数%1前面那个参数，当然就是批处理文件名（包括路径）。
以上就是批处理中的一些系统变量,另外还有一些变量,他们也表示一些功能,
FOR命令中的那些就是,FOR变量已经说过,就不讲了.

**二、自定义变量**

故名思意,自定义变量就是由我们来给他赋予值的变量
要使用自定义变量就得使用set命令了,看例子.

> @echo off
> set var=我是值
> echo %var%
> pause

保存为BAT执行,我们会看到CMD里返回一个 "我是值"
var为变量名,=号右变的是要给变量的值
这就是最简单的一种设置变量的方法了
如果我们想让用户手工输入变量的值,而不是在代码里指定,可以用用set命令的/p参数
例子:

> @echo off
> set /p var=请输入变量的值
> echo %var%
> pause

var变量名 =号右边的是提示语,不是变量的值
变量的值由我们运行后自己用键盘输入!

一、交互界面设计

没啥说的，看看高手设计的菜单界面吧：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``cls``title 终极多功能修复``:menu``cls``color 0A``echo``.``echo` `==============================``echo` `请选择要进行的操作，然后按回车``echo` `==============================``echo``.``echo` `1.网络修复及上网相关设置,修复IE,自定义屏蔽网站``echo``.``echo` `2.病毒专杀工具，端口关闭工具,关闭自动播放``echo``.``echo` `3.清除所有多余的自启动项目，修复系统错误``echo``.``echo` `4.清理系统垃圾,提高启动速度``echo``.``echo` `Q.退出``echo``.``echo``.``:cho``set` `choice=``set` `/p choice= 请选择:``IF NOT ``"%choice%"``==``""` `SET` `choice=%choice:~0,1%``if /i ``"%choice%"``==``"1"` `goto ip``if /i ``"%choice%"``==``"2"` `goto setsave``if /i ``"%choice%"``==``"3"` `goto kaiji``if /i ``"%choice%"``==``"4"` `goto clean``if /i ``"%choice%"``==``"Q"` `goto endd``echo` `选择无效，请重新输入``echo``.``goto cho`
```

只要学完本教程前面的章节，上面的程序应该能看懂了。

**二、if…else…条件语句**

前面已经谈到，DOS条件语句主要有以下形式
IF [NOT] ERRORLEVEL number command
IF [NOT] string1==string2 command
IF [NOT] EXIST filename command
增强用法：IF [/I] string1 compare-op string2 command
增强用法中加上/I就不区分大小写了!
增强用法中还有一些用来判断数字的符号：

EQU - 等于
NEQ - 不等于
LSS - 小于
LEQ - 小于或等于
GTR - 大于
GEQ - 大于或等于

上面的command命令都可以用小括号来使用多条命令的组合，包括else子句，组合命令中可以嵌套使用条件或循环命令。

例如:

IF EXIST filename (
del filename
) ELSE (
echo filename missing
)

也可写成：
if exist filename (del filename) else (echo filename missing)
但这种写法不适合命令太多或嵌套命令的使用。注意：else必须和if在同一行，或者和if最后的括号在同一行，如： ......) ELSE (......。在括号那换行程序认为是一条语句。

**三、循环语句**

1、指定次数循环
FOR /L %variable IN (start,step,end) DO command [command-parameters]

组合命令：
FOR /L %variable IN (start,step,end) DO (
Command1
Command2
……
)

2、对某集合执行循环语句。
FOR %%variable IN (set) DO command [command-parameters]

%%variable 指定一个单一字母可替换的参数。
(set) 指定一个或一组文件。可以使用通配符。
command 对每个文件执行的命令，可用小括号使用多条命令组合。

FOR /R [[drive:]path] %variable IN (set) DO command [command-parameters]

检查以 [drive:]path 为根的目录树，指向每个目录中的
FOR 语句。如果在 /R 后没有指定目录，则使用当前
目录。如果集仅为一个单点(.)字符，则枚举该目录树。

同前面一样，command可以用括号来组合：
FOR /R [[drive:]path] %variable IN (set) DO (
Command1
Command2
……
commandn
)

3、条件循环
上面的循环结构是用for命令来实现的，for命令循环有一个缺点，就是整个循环被当作一条命令语句，涉及到变量延迟的问题。
利用goto语句和条件判断，dos可以实现条件循环，很简单啦，看例子：

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``set` `var=0``rem ************循环开始了``:continue``set` `/a var+=1``echo` `第%var%次循环``if %var% lss 100 goto continue``rem ************循环结束了``echo` `循环执行完毕``pause`
```

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``set` `var=100``rem ************循环开始了``:continue``echo` `第%var%次循环``set` `/a var-=1``if %var% gtr 0 goto continue``rem ************循环结束了``echo` `循环执行完毕``pause`
```

**四、子程序**

在批处理程序中可以调用外部可运行程序，比如exe程序，也可调用其他批处理程序，这些也可以看作子程序，但是不够方便，如果被调用的程序很多，就显得不够简明了，很繁琐。
在windowsXP中，批处理可以调用本程序中的一个程序段，相当于子程序，这些子程序一般放在主程序后面。

子程序调用格式：
CALL :label arguments

子程序语法：
:label
command1
command2
......
commandn
goto :eof

在子程序段中，参数%0指标签:label

子过程一般放在最后，并且注意在主程序最后要加上exit或跳转语句，避免错误的进入子过程。

子程序和主程序中的变量都是全局变量，其作用范围都是整个批处理程序。

传至子程序的参数在call语句中指定，在子程序中用%1、%2至%9的形式调用，而子程序返回主程序的数据只需在调用结束后直接引用就可以了，当然也可以指定返回变量，请看下面的例子。

子程序例1：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``call :sub return``echo` `子程序返回值：%return%``pause``goto :eof` `:sub``set` `%1=你好``goto :eof`
```

运行结果：你好

子程序例2：设计一个求多个整数相加的子程序

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``set` `sum=0``call :sub 10 20 35 40 50``echo` `数据求和结果：%sum%``pause``goto :eof` `:sub``rem 参数1为返回变量名称``set` `/a sum+=%1``shift /1 ``if not ``"%1"``==``""` `goto sub``goto :eof`
```

运行结果：155

**五、用ftp命令实现自动下载**

ftp是常用的下载工具，ftp界面中有40多个常用命令，自己学习了，不介绍了。这里介绍如何用dos命令行调用ftp命令，实现ftp自动登录，并上传下载，并自动退出ftp程序。
其实可以将ftp命令组合保存为一个文本文件，然后用以下命令调用即可。

ftp -n -s:[[drive:]path]filename

上面的filename为ftp命令文件，包括登录IP地址，用户名、密码、操作命令等
例：

[?](https://www.jb51.net/article/151923.htm#)

```
`open 90.52.8.3 ＃打开ip``user iware ＃用户为iware``password8848 ＃密码``bin ＃二进制传输模式``prompt``cd` `tmp1 ＃切换至iware用户下的tmp1目录``pwd``lcd d:\download ＃本地目录``mget * ＃下载tmp1目录下的所有文件``bye ＃退出ftp`
```

**六、用7-ZIP实现命令行压缩和解压功能**

语法格式：（详细情况见7-zip帮助文件，看得头晕可以跳过，用到再学）
7z <command> [<switch>...] <base_archive_name> [<arguments>...]

7z.exe的每个命令都有不同的参数<switch>,请看帮助文件
<base_archive_name>为压缩包名称
<arguments>为文件名称，支持通配符或文件列表

其中，7z是至命令行压缩解压程序7z.exe，<command>是7z.exe包含的命令，列举如下：

a： Adds files to archive. 添加至压缩包
a命令可用参数：
-i (Include)
-m (Method)
-p (Set Password)
-r (Recurse)
-sfx (create SFX)
-si (use StdIn)
-so (use StdOut)
-ssw (Compress shared files)
-t (Type of archive)
-u (Update)
-v (Volumes)
-w (Working Dir)
-x (Exclude)

b： Benchmark
d： Deletes files from archive. 从压缩包中删除文件
d命令可用参数：
-i (Include)
-m (Method)
-p (Set Password)
-r (Recurse)
-u (Update)
-w (Working Dir)
-x (Exclude)

e： Extract解压文件至当前目录或指定目录
e命令可用参数：
-ai (Include archives)
-an (Disable parsing of archive_name)
-ao (Overwrite mode)
-ax (Exclude archives)
-i (Include)
-o (Set Output Directory)
-p (Set Password)
-r (Recurse)
-so (use StdOut)
-x (Exclude)
-y (Assume Yes on all queries)

l： Lists contents of archive.
t： Test
u： Update

x： eXtract with full paths用文件的完整路径解压至当前目录或指定目录
x命令可用参数：
-ai (Include archives)
-an (Disable parsing of archive_name)
-ao (Overwrite mode)
-ax (Exclude archives)
-i (Include)
-o (Set Output Directory)
-p (Set Password)
-r (Recurse)
-so (use StdOut)
-x (Exclude)
-y (Assume Yes on all queries)

**七、调用VBScript程序**

使用 Windows 脚本宿主，可以在命令提示符下运行脚本。CScript.exe 提供了用于设置脚本属性的命令行开关。

用法：CScript 脚本名称 [脚本选项...] [脚本参数...]
选项：
//B 批模式：不显示脚本错误及提示信息
//D 启用 Active Debugging
//E:engine 使用执行脚本的引擎
//H:CScript 将默认的脚本宿主改为 CScript.exe
//H:WScript 将默认的脚本宿主改为 WScript.exe （默认）
//I 交互模式（默认，与 //B 相对)
//Job:xxxx 执行一个 WSF 工作
//Logo 显示徽标（默认）
//Nologo 不显示徽标：执行时不显示标志
//S 为该用户保存当前命令行选项
//T:nn 超时设定秒：允许脚本运行的最长时间
//X 在调试器中执行脚本
//U 用 Unicode 表示来自控制台的重定向 I/O

“脚本名称”是带有扩展名和必需的路径信息的脚本文件名称，如d:/admin/vbscripts/chart.vbs。
“脚本选项和参数”将传递给脚本。脚本参数前面有一个斜杠 (/)。每个参数都是可选的；但不能在未指定脚本名称的情况下指定脚本选项。如果未指定参数，则 CScript 将显示 CScript 语法和有效的宿主参数。

**八、将批处理转化为可执行文件**

由于批处理文件是一种文本文件，任何人都可以对其进行随便编辑，不小心就会把里面的命令破坏掉，所以如果将其转换成.com格式的可执行文件，不仅执行效率会大大提高，而且不会破坏原来的功能，更能将优先级提到最高。Bat2Com就可以完成这个转换工作。
小 知识：在DOS环境下，可执行文件的优先级由高到低依次为.com>.exe>.bat>.cmd，即如果在同一目录下存在文件名相同 的这四类文件，当只键入文件名时，DOS执行的是name.com，如果需要执行其他三个文件，则必须指定文件的全名，如name.bat。

这是一个只有5.43K大小的免费绿色工具，可以运行在纯DOS或DOS窗口的命令行中，用法：Bat2Com
FileName，这样就会在同一目录下生成一个名为FileNme.com的可执行文件，执行的效果和原来的.bat文件一样。

**九、时间延迟**

本条参考引用[英雄]教程
什么是时间延迟？顾名思义，就是执行一条命令后延迟一段时间再进行下一条命令。
延迟的应用见下节：“模拟进度条”。
1、利用ping命令延时
例：

> @echo off
> echo 延时前：%time%
> ping /n 3 127.0.0.1 >nul
> echo 延时后：%time%
> pause

解说：用到了ping命令的“/n”参数，表示要发送多少次请求到指定的ip。本例中要发送3次请求到本机的ip（127.0.0.1）。127.0.0.1可简写为127.1。“>nul”就是屏蔽掉ping命令所显示的内容。

2、利用for命令延时

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `延时前：%time%``for /l %%i in (1,1,5000) do ``echo` `%%i>nul``echo` `延时后：%time%``pause`
```

解说：原理很简单，就是利用一个计次循环并屏蔽它所显示的内容来达到延时的目的。

3、利用vbs延迟函数，精确度毫秒，误差1000毫秒内

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `%time%``call :delay 5000``echo` `%time%``pause` `exit``:delay``echo` `WScript.``Sleep` `%1>delay.vbs``CScript //B delay.vbs``del` `delay.vbs``goto :eof`
```

运行显示：

10:44:06.45
10:44:11.95
请按任意键继续. . .

上面的运行结果显示实际延时了5500毫秒，多出来的500毫秒时建立和删除临时文件所耗费的时间。误差在一秒之内。

**4、仅用批处理命令实现任意时间延迟，精确度10毫秒，误差50毫秒内**

仅用批处理命令就可以实现延迟操作。

例：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``set` `/p delay=请输入需延迟的毫秒数：``set` `TotalTime=0``set` `NowTime=%time%``::读取起始时间，时间格式为：13:01:05.95``echo` `程序开始时间：%NowTime%``:delay_continue``set` `/a minute1=1``%``NowTime:~3,2%-100``::读取起始时间的分钟数``set` `/a second1=1``%``NowTime:~-5,2%%NowTime:~-2``%``0-100000``::将起始时间的秒数转为毫秒``set` `NowTime=%time%``set` `/a minute2=1``%``NowTime:~3,2%-100``:: 读取现在时间的分钟数``set` `/a second2=1``%``NowTime:~-5,2%%NowTime:~-2``%``0-100000``::将现在时间的秒数转为毫秒``set` `/a TotalTime+=(%minute2%-%minute1%+60)%%60*60000+%second2%-%second1%``if %TotalTime% lss %delay% goto delay_continue``echo` `程序结束时间：%time%``echo` `设定延迟时间：%delay%毫秒``echo` `实际延迟时间：%TotalTime%毫秒``pause`
```

运行显示：

请输入需延迟的毫秒数：6000
程序开始时间：15:32:16.37
程序结束时间：15:32:22.37
设定延迟时间：6000毫秒
实际延迟时间：6000毫秒
请按任意键继续. . .

实现原理：首先设定要延迟的毫秒数，然后用循环累加时间，直到累加时间大于等于延迟时间。

误差：windows系统时间只能精确到10毫秒，所以理论上有可能存在10毫秒误差。
经测试，当延迟时间大于500毫秒时，上面的延迟程序一般不存在误差。当延迟时间小于500毫秒时，可能有几十毫秒误差，为什么？因为延迟程序本身也是有运行时间的，同时系统时间只能精确到10毫秒。

为了方便引用，可将上面的例子改为子程序调用形式：

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``echo` `程序开始时间：%Time%``call :delay 10``echo` `实际延迟时间：%totaltime%毫秒``echo` `程序结束时间：%time%``pause``exit` `::-----------以下为延时子程序--------------------``:delay``@``echo` `off``if ``"%1"``==``""` `goto :eof``set` `DelayTime=%1``set` `TotalTime=0``set` `NowTime=%time%``::读取起始时间，时间格式为：13:01:05.95``:delay_continue``set` `/a minute1=1``%``NowTime:~3,2%-100``set` `/a second1=1``%``NowTime:~-5,2%%NowTime:~-2``%``0-100000``set` `NowTime=%time%``set` `/a minute2=1``%``NowTime:~3,2%-100``set` `/a second2=1``%``NowTime:~-5,2%%NowTime:~-2``%``0-100000``set` `/a TotalTime+=(%minute2%-%minute1%+60)%%60*60000+%second2%-%second1%``if %TotalTime% lss %DelayTime% goto delay_continue``goto :eof`
```

**十、模拟进度条**

下面给出一个模拟进度条的程序。如果将它运用在你自己的程序中，可以使你的程序更漂亮。

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``mode con cols=113 lines=15 &color 9f``cls``echo``.``echo` `程序正在初始化. . . ``echo``.``echo` `┌──────────────────────────────────────┐``set``/p= ■`for /L %%i in (1 1 38) do ``set` `/p a=■nul``echo` `100%%``echo` `└──────────────────────────────────────┘``pause`
```

解说：“set /p a=■<nul”的意思是：只显示提示信息“■”且不换行，也不需手工输入任何信息，这样可以使每个“■”在同一行逐个输出。“ping /n 0 127.1>nul”是输出每个“■”的时间间隔，ping /n 0表示不执行这个命令，所以会比ping出去的时间更短，也就是即每隔多少时间最短输出一个“■”。当然你也可以改为1或2或3等使时间延长

PS:上面的代码执行太快了，并且第一个出现的节奏和后面的不协调，我稍微修改了点，如下：

[?](https://www.jb51.net/article/151923.htm#)

```
`echo``.``echo` `┌──────────────────────────────────────┐``ping 127.0.0.1 >nul /n 1 & ``set` `/p=`for /L %%i in (1 1 39) do ``set` `/p a=■nul``echo` `100%%``echo` `└──────────────────────────────────────┘``pause`
```

**十一、特殊字符的输入及应用**

开始 -> 运行 -> 输入cmd -> edit -> ctrl+p（意思是允许输入特殊字符）-> 按ctrl+a将会显示笑脸图案。

（如果要继续输入特殊字符请再次按ctrl+p，然后ctrl+某个字母）

以上是特殊字符的输入方法，选自[英雄]教程，很管用的。也就是用编辑程序edit输入特殊字符，然后保存为一文本文件，再在windows下打开此文件，复制其中的特殊符号即可。

一些简单的特殊符号可以在dos命令窗口直接输入，并用重定向保存为文本文件。
例：

C:>ECHO ^G>temp.txt
“^G”是用Ctrl＋G或Alt＋007输入(按住Alt后，只能按小键盘的数字)，输入多个^G可以产生多声鸣响。

特殊字符的应用也很有意思，这里仅举一例：退格键(输入方法：开始 -> 运行 -> 输入cmd -> edit -> ctrl+p ->退格键)

退格键表示删除左边的字符，此键不能在文档中正常输入，但可以通过edit编辑程序录入并复制出来。即“”。

利用退格键，配合空格覆盖，可以设计闪烁文字效果

例：文字闪烁，可以使用Ctrl+C组合键来强行终运行

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``:start``set``/p=床前明月光`::显示文字，光标停于行尾``ping ``-n` `0 127.0.0.1>nul``::设置延迟时间` `set` `/p a=`:: 输出一些退格符将光标置于该行的最左端（退格符的数量可以自己调整）。` `ping ``-n` `0 127.0.0.1>nul``::设置延迟时间` `set` `/p a= `::输出空格将之前输出的文字覆盖掉。` `set` `/p a=`::再次输出退格符将光标置于该行的最左端，这里的退格符数量一定不能比前面的` `空格数少，否则光标不能退到最左端。` `ping ``-n` `0 127.0.0.1>nul``::设置延迟时间` `goto start`
```

解说：主要是利用set命令的/p，表示后等号面的字符都是提示字符，然后在用退格键，让光标置于该行的最左端，但是原来的文字还在，然后使用空格作为输入提示符，所以就会覆盖前面的文字，然后再次输出退格符将光标置于该行的最左端，循环执行。如果你把ping命令的次数改为4，使延迟增长，就能看到光标的位置变化了。

例：输出唐诗一首，每行闪动多次

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``setlocal enabledelayedexpansion` `set` `str=床前明月光 疑是地上霜 举头望明月 低头思故乡``::定义字符串str``for %%i in (%str%) do (``rem 由于str中含有空格，则以空格为分隔符将str中的每一个部分依次赋给变量%%i。``set` `char=%%i``echo``.``echo``.``for /l %%j in (0,1,5) do (``set``/p=!char:~%%j,1!`rem 依次取出变量char中的每一个字符，并显示。``ping ``-n` `0 127.0.0.1>nul``rem 设置输出每个字符的时间延迟。``)``call :hero %%i``)``pause>nul``exit` `:hero``for /l %%k in (1,1,10) do (``ping /n 0 127.0.0.1>nul``set` `/p a=`set` `/p a= `set` `/p a=`ping /n 0 127.0.0.1>nul``set` `/p a=%1`)``::文字闪动``goto :eof`
```

**十二、随机数（%random%）的应用技巧**

%RANDOM% 系统变量 返回 0 到 32767 之间的任意十进制数字。由 Cmd.exe 生成。

2的15次方等于32768，上面的0～32767实际就是15位二进制数的范围。

那么，如何获取100以内的随机数呢？很简单，将%RANDOM%按100进行求余运算即可，见例子。

例：生成5个100以内的随机数

> @echo off
> setlocal enabledelayedexpansion
> for /L %%i in (1 1 5) do (
> set /a randomNum=!random!%%100
> echo 随机数：!randomNum!
> )
> pause

运行结果：（每次运行不一样）
随机数：91
随机数：67
随机数：58
随机数：26
随机数：20
请按任意键继续. . .

求余数运算set /a randomNum=!random!%%100中的100可以是1～32768之间的任意整数。

总结：利用系统变量%random%，求余数运算%%，字符串处理等，可以实现很多随机处理。

通过上面的学习，我们知道，%random%可以产生0到32767之间的随机数，但是，如何才能得到一定范围内的随机数呢？
我们可以使用通用的算法公式如下：
　　通用的公式%random%%%(max-min+1)+min来产生[min,max]区间里的随机数，
注：批处理中求模得用两个%%符号。
　　比如，我们想获得4到12之间的随机数，就可以这样来使用，代码如下：

[?](https://www.jb51.net/article/151923.htm#)

```
`@REM 产生10个[4,12]间的随机数 ``@``echo` `off ``REM 启用延迟环境变量扩展 ``setlocal enabledelayedexpansion ``REM 设置随机数的最小和最大值以及求模用的变量 ``set` `min=4 ``set` `max=12 ``set` `/a mod=!max!-!min!+1` `for /l %%i in (1,1,10) do ( ``REM 产生[min,max]之间的随机数 ``set` `/a ``r``=!random!%%!mod!+!min! ``echo``. ``echo` `随机数%%i：!``r``!)`
```

详细出处参考：[//www.jb51.net/article/36489.htm](https://www.jb51.net/article/36489.htm)

思考题目：生成给定位数的随机密码
解答思路：将26个英文字母或10数字以及其它特殊字符组成一个字符串，随机抽取其中的若干字符。

参考答案1：（简单）

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``call :randomPassword 5 pass1 pass2``echo` `%pass1% %pass2% ``pause``exit` `:randomPassword``::---------生成随机密码``::---------%1为密码长度，%2及以后为返回变量名称``::--------``-for``命令最多只能区分31个字段``@``echo` `off``set` `password_len=%1``if not defined password_len goto :eof``if %password_len% lss 1 goto :eof``set` `wordset=a b c d e f g ``h` `i j k l m n o p q ``r` `s t u v w x y z``set` `return=``set` `num=0``:randomPassword1``set` `/a num+=1``set` `/a numof=%random%%%26+1``for /f ``"tokens=%numof% delims= "` `%%i in (``"%wordset%"``) do ``set` `return=%return%%%i``if %num% lss %password_len% goto randomPassword1``if not ``"%2"``==``""` `set` `%2=%return%``shift /2``if not ``"%2"``==``""` `goto randomPassword``goto :eof`
```

参考答案2：（最优）

[?](https://www.jb51.net/article/151923.htm#)

```
`@``echo` `off``call :randomPassword 6 pass1 pass2 pass3``echo` `%pass1% %pass2% %pass3%``pause``exit` `:randomPassword``::---------生成随机密码``::---------%1为密码长度，%2及以后为返回变量名称``::--------``-goto``循环、变量嵌套、命令嵌套``@``echo` `off``if ``"%1"``==``""` `goto :eof``if %1 lss 1 goto :eof``set` `password_len=%1``set` `return=``set` `wordset=abcdefghijklmnopqrstuvwxyz023456789_``::---------------------------循环``:randomPassword1``set` `/a numof=%random%%%36 ::---生成0-35之间的随即数``call ``set` `return=%return%%%wordset:~%numof%,1%% ::---在wordset变量中，从的随即生成的0-35的下一个取出一个字符``set` `/a password_len-=1``if %password_len% gtr 0 goto randomPassword1``::---------------------------循环``if not ``"%2"``==``""` `set` `%2=%return%``shift /2``if not ``"%2"``==``""` `goto randomPassword``goto :eof`
```

说明：本例涉及到变量嵌套和命令嵌套的应用，见后。

**十三、变量嵌套 与 命令嵌套**

和其它编程语言相比，dos功能显得相对简单，要实现比较复杂的功能，需要充分运用各种技巧，变量嵌套与命令嵌套就是此类技巧之一。

先复习一下前面的“字符串截取”的关键内容：

**********************************************
截取功能统一语法格式为：%a:~[m[,n]]%
**********************************************
方括号表示可选，%为变量标识符，a为变量名，不可少，冒号用于分隔变量名和说明部分，符号～可以简单理解为“偏移”即可，m为偏移量（缺省为0），n为截取长度（缺省为全部）。

百分号如果需要当成单一字符，必须写成%%

以上是dos变量处理的通用格式，如果其中的m、n为变量，那么这种情况就是变量嵌套了。

比如设变量word为“abcdefghij”，变量num为“123456789”
%word:~4,1%为e，其中4可以从变量num中取值，即%num:~3,1%，写成组合形式如下：
%word:~%num:~3,1%,1% 经测试这种写法不能正确执行，写成%word:~(%num:~3,1%),1%同样不行，那么，怎么实现这种变量嵌套呢？这就必须结合命令嵌套。

什么是命令嵌套呢？简单的说，首先用一条dos命令生成一个字符串，而这个字符串是另一条dos命令，用call语句调用字符串将其执行，从而得到最终结果。

例：用call语句实现命令嵌套

> @echo off
> set str1=aaa echo ok bbb
> echo 初始字符串：%str1%
> echo 生成命令字符串如下：
> echo %str1:~4,7%
> echo 运行命令字符串生成最终结果为：
> call %str1:~4,7%
> pause

运行显示：
初始字符串：aaa echo ok bbb
生成命令字符串如下：
echo ok
运行命令字符串生成最终结果为：
ok
请按任意键继续. . .

# 这是一个很简单的教程

桌面、迅雷下载文件夹、还有QQ文件接收目录都是我平时存放很多文件的地方，但是久了这几个文件夹就会变得很杂，于是我想到了应该可以写一个脚本让这些文件归档，便于以后保存和查找。
 顺便写了个教程。

# 首先，新建一个txt文件

![img](https:////upload-images.jianshu.io/upload_images/7123916-2fd1588557f97be3.png?imageMogr2/auto-orient/strip|imageView2/2/w/167/format/webp)

image.png

# 先说一下代码：

下面的代码其实就只是一个**move语句** 和 **通配符" \* "**而已

## move语句

move语句的用法是：
 `move "[文件名]" [绝对路径]`*（方括号以及它里面的内容都是可以自由输入的）*

## 通配符“ * ”，

例如我要将当前目录的所有的txt文件夹移动到E盘下的“文档”文件夹里的“txt”文件夹
 那就可以写这样一行代码：
 `move "*.txt" E:\文档\txt\`
 *表示任意字符，.txt是文件名后缀 然后空格，接下来是目标文件夹的绝对路径
 根据自己的需求，写几行move语句即可。

# pause

按任意键退出程序。

# 下面是一段实例

这我个人的存放路径，所以你要根据自己的需要改一下路径，也可以创建跟我一样的路径，推荐前一种做法。

```rust
move "*.txt" E:\文档\txt\

move "*.xlsx" E:\文档\xlsx\
move "*.xls" E:\文档\xlsx\

move "*.docx" E:\文档\word\
move "*.doc" E:\文档\word\

move "*.pdf" E:\文档\电子书\
move "*.mobi" E:\文档\电子书\
move "*.epub" E:\文档\电子书\
move "*.azw3" E:\文档\电子书\

move "*.pptx" E:\文档\ppt\
move "*.ppt" E:\文档\ppt\

move "*.exe" E:\软件\安装包\

move "*.iso" E:\其他\

move "*.rmvb" E:\视频\

move "*.zip" E:\压缩包\
move "*.rar" E:\压缩包\

move "*.jpg" E:\图片\
move "*.png" E:\图片\
pause
```

# 代码输入之后的保存

代码输入之后，点击记事本的文件→另存为：



![img](https:////upload-images.jianshu.io/upload_images/7123916-7a81f60afee680ff.png?imageMogr2/auto-orient/strip|imageView2/2/w/428/format/webp)

image.png

存放在桌面上，记得保存的文件名后缀是".bat"



![img](https:////upload-images.jianshu.io/upload_images/7123916-ab1570b9eab8794f.png?imageMogr2/auto-orient/strip|imageView2/2/w/944/format/webp)

image.png

# 运行

然后你会看到桌面上多了一个bat文件，双击运行。



![img](https:////upload-images.jianshu.io/upload_images/7123916-0a76862d7cf29af1.png?imageMogr2/auto-orient/strip|imageView2/2/w/602/format/webp)

image.png

会看到上边的画面（运行结果因目录状态不同而不同，我归档过了所以找不到文件），然后你就会发现你桌面上的很多文件都不见了，并且可以在你设置的目标目录找到它们。
 接下来你可以把这个bat文件放到迅雷下载目录和QQ文件接收目录等等所有需要整理文件的文件夹运行，就能一键归档文件啦！