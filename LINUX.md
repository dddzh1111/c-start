# LINUX

## 学习的点：

1. 务必学会vi文书编辑器： Linux的文书编辑器多到会让你数到生气！不过，vi却是强烈建议要先学习的！ 这是因为vi会被很多软件所调用，加上所有的Unix like系统上面都有vi，所以你一定要学会才好！
2. Shell与Shell Script的学习： 其实鸟哥上面一直谈到的“命令行”说穿了就是一个名为shell的软件啦！既然要玩命令行，当然就是要会使用shell的意思。 但是shell上面的数据太多了，包括“正则表达式”、“管线命令”与“数据流重导向”等等，真的需要了解比较好呦！ 此外，为了帮助你未来的管理服务器的便利性，shell scripts也是挺重要的！要学要学！
3. 一定要会软件管理员： 因为玩Linux常常会面临得要自己安装驱动程序或者是安装额外软件的时候，尤其是嵌入式设备或者是学术研究单位等。 这个时候Tarball/RPM/DPKG/YUM/APT等软件管理员的安装方式的了解，对你来说就重要到不行了！
4. 网络基础的创建： 如果上面你都通过了，那么网络的基础就是下一阶段要接触的咚咚，这部份包含了“IP概念”“路由概念”等等；
5. 如果连网络基础都通过了，那么网站的架设对你来说，简直就是“太简单啦！”

在一些基础知识上，可能的话，当然得去书店找书来读啊！ 如果您想要由网络上面阅读的话，那么这里推荐一下由Netman大哥评论员的Study-Area里面的基础文章，相当的实用！

- [计算机基础 （http://www.study-area.org/compu/compu.htm）](http://www.study-area.org/compu/compu.htm)
- [网络基础 （http://www.study-area.org/network/network.htm）](http://www.study-area.org/network/network.htm)



## 系统命令

pwd :显示当前路径

ls （list 列表） :查看目录

​        total 来表总大小

​       -l  垂直罗列

​       -a 显示隐藏文件

​         . 代表 隐藏文件

​       -h 显示按照KB

​         . 当前目录

​         .. 上一级目录

通配符 *  ls *txt txt类型的所有文件 ( ***)**

​          •test*，表示匹配任何以test开头的内容

​          •*test，表示匹配任何以test结尾的内容

​           •* test*，表示匹配任何包含test的内容

​             ?   ls ???.txt 模糊查询

​             【】 ls [1234]23.txt 规定查找范围1234内

​                         【1-4】【a-z】

cd ：进入目录文件

​         cd .. 返回上一级路径

​         cd ~ 直接返回home

​         cd - 与上一个目录切换如同Tab+Alt

tab ：具有自动查找目录功能

绝对路径：以根目录为起点，描述路径的一种写法，路径描述以/开头

相对路径：以当前目录为起点，描述路径的一种写法，路径描述无需以/开头



## 文件命令

touch 创建文件需要带后缀名

touch bb.txt 

touch . bb.txt 创建隐藏文件



mkdir 创建目录

mkdir one/news  创建多级目录错误写法

**mkdir** **-p**  创建多级目录



rm 移除文件

​      -r移除目录（无法还原）

​      -d 移除目录（无法删除多级目录 -r可以）

​      -f  强制删除 •普通用户删除内容不会弹出提示，只有root管理员用户删除内容会有提示

如下命令，请千万千万不要在root管理员用户下执行：

rm -rf /

rm -rf /*

效果等同于在Windows上执行C盘格式化。



**cat**  查看文件内容

more 查看文件内容

•cat是直接将内容全部显示出来

•more支持翻页，如果文件内容过多，可以一页页的展示



mv   移动（剪切）文件   目录

cp  复制文件 / 目录

•-r选项，可选，用于复制文件夹使用，表示递归



## 查找命令

which 查看所使用的一系列命令的程序文件存放在哪里 



**find **按文件名查找文件

1.fine -name 所有路径文件中查找

2.使用通配符查找

3.按文件大小查找

-size +/- n(k,M,G)

•+、- 表示大于和小于

•n表示大小数字

•kMG表示大小单位，k(小写字母)表示kb，M表示MB，G表示GB 



grep 过滤筛选

grep "123" 1.txt (从1.txt文件中过滤有123进行输出)

grep -n "123" 1.txt (从1.txt文件中过滤有123进行输出并显示行号)



wc 统计文件的行数、单词数量等

•选项，-c，统计bytes数量

•选项，-m，统计字符数量

•选项，-l，统计行数

•选项，-w，统计单词数量



管道符  |

左边的结果给予右边 | 右边命令   



echo 在命令行内输出指定内容

echo "hello world" 遇见多条语句的使用“ ”好区分



反引号 `

echo `pwd 被`包围的内容，会被作为命令执行，而非普通字符



重定向符：>和>>

•>，将左侧命令的结果，覆盖写入到符号右侧指定的文件中

•>>，将左侧命令的结果，追加写入到符号右侧指定的文件中

echo "hello" > 1.txt



tail 可以查看文件尾部内容，跟踪文件的最新更改

•选项，-f，表示持续跟踪

持续运行

ctrl + c 停止命令持续运行

•选项, -num，表示，查看尾部多少行，不填默认10行

 tail -5  1.txt 查看尾部5行



## vi\vim编辑器

三种命令模式

命令模式（Command mode）

  命令模式下，所敲的按键编辑器都理解为命令，以命令驱动执行不同的功能。

  此模型下，不能自由进行文本编辑。



输入模式（Insert mode）

  也就是所谓的编辑模式、插入模式。

  此模式下，可以对文件内容进行自由编辑。



底线命令模式（Last line mode）

  以：开始，通常用于文件的保存、退出。



## root 用户

root（超级管理员）用户拥有最大的系统操作权限，而普通用户在许多地方的权限是受限的。

•普通用户的权限，一般在其HOME目录内是不受限的

•一旦出了HOME目录，大多数地方，普通用户仅有只读和执行权限，无修改权限



su      用于账户切换的系统命令

su - root



sudo  为普通的命令授权，临时以root身份执行

•在其它命令之前，带上sudo，即可为这一条命令临时赋予root授权

•但是并不是所有的用户，都有权利使用sudo，我们需要为普通用户配置sudo认证

普通用户配置sudo认证：

•切换到root用户，执行visudo命令，会自动通过vi编辑器打开：/etc/sudoers

o ：添加命令

输入用户名![1684037890621](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684037890621.png) 

NOPASSWD --  不需要密码

执行完成 esq --- ：--wq 保存并退出



## 用户和用户组

Linux中关于权限的管控级别有2个级别，分别是：

•针对用户的权限控制

•针对用户组的权限控制



•创建用户组

groupadd 用户组名

•删除用户组

groupdel 用户组名



用户管理

•创建用户

useradd [-g -d] 用户名

•选项：-g指定用户的组，不指定-g，会创建同名组并自动加入，指定-g需要组已经存在，如已存在同名组，必须使用-g

•选项：-d指定用户HOME路径，不指定，HOME目录默认在：/home/用户名



•删除用户

userdel [-r] 用户名

•选项：-r，删除用户的HOME目录，不使用-r，删除用户时，HOME目录保留



•查看用户所属组

id [用户名]

•参数：用户名，被查看的用户，如果不提供则查看自身



•修改用户所属组

usermod -aG 用户组 用户名，将指定用户加入指定用户组



getent命令，可以查看当前系统中有哪些用户

语法： getent passwd

共有7份信息，分别是：

![1684044633273](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684044633273.png)

用户名:密码(x):用户ID:组ID:描述信息(无用):HOME目录:执行终端(默认bash)



getent命令，同样可以查看当前系统中有哪些用户组

语法：getent group

包含3份信息，组名称:组认证(显示为x):组ID



## 查看权限控制

![1684119809449](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684119809449.png)

•r表示读权限

•w表示写权限

•x表示执行权限



针对文件、文件夹的不同，rwx的含义有细微差别

•r，针对文件可以查看文件内容

•针对文件夹，可以查看文件夹内容，如ls命令

•w，针对文件表示可以修改此文件

•针对文件夹，可以在文件夹内：创建、删除、改名等操作

•x，针对文件表示可以将文件作为程序执行

•针对文件夹，表示可以更改工作目录到此文件夹，即cd进入



## 权限修改

只有文件所有者拥有对权限的修改

chmod  修改文件、文件夹的权限信息

•选项：-R，对文件夹内的全部内容应用同样的操作

chmod u=rwx,g=rwx,o=rwx 文件名

u:user g:group o:other



方便替代：chmod 421 文件名：

数字的细节如下：r记为4，w记为2，x记为1，可以有：

•0：无任何权限，  即 ---

•1：仅有x权限，  即 --x

•2：仅有w权限  即 -w-

•3：有w和x权限  即 -wx

•4：仅有r权限  即 r--

•5：有r和x权限  即 r-x

•6：有r和w权限  即 rw-

•7：有全部权限  即 rwx



chown  可以修改文件、文件夹的所属用户和用户组

![1684132589766](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684132589766.png)

普通用户无法修改所属为其它用户或组，所以此命令只适用于root用户执行

root需要进入到home里的用户读取文件

•选项，-R，同chmod，对文件夹内全部内容应用相同规则

•选项，用户，修改所属用户

•选项，用户组，修改所属用户组

•:用于分隔用户和用户组



## ————————————-



## 快捷键

\1. ctrl + c 强制停止

\2. ctrl + d 退出登出

\3. history 查看历史命令

\4. !命令前缀，自动匹配上一个命令

\5. ctrl + r，搜索历史命令

\6. ctrl + a | e，光标移动到命令开始或结束

\7. ctrl + ← | →，左右跳单词

\8. ctrl + l 或 clear命令 清屏



## 软件安装

yum：RPM包软件管理器，用于自动化安装配置Linux软件，并可以自动解决依赖问题。

•选项：-y，自动确认，无需手动确认安装或卸载过程

•install：安装

•remove：卸载

•search：搜索

CentOS使用yum管理器，Ubuntu使用apt管理器

用法和yum一致，同样需要root权限

•apt install wget，安装wget

•apt remove wget，移除wget

•apt search wget，搜索wget



systemctl命令控制软件的启动和关闭

![1684137613437](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684137613437.png)

•第三方软件，如果自动注册了可以被systemctl控制（需要yum下载）



## 软连接

![1684139393021](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684139393021.png)

•-s选项，创建软连接

•参数1：被链接的文件或文件夹

•参数2：要链接去的目的地



## 日期和时间

date： 在命令行中查看系统的时间![1684207410866](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684207410866.png)

•-d 按照给定的字符串显示日期，一般用于日期计算

•格式化字符串：通过特定的字符串标记，来控制显示的日期格式

•**%Y   年**

•**%y   年份后两位数字 (00..99)**

•**%m   月份 (01..12)**

•**%d   日 (01..31)**

•**%H**   **小时** **(00..23)**

•**%M**   **分钟** **(00..59)**

•**%S   秒 (00..60)**

•**%s   自 1970-01-01 00:00:00 UTC** **到现在的秒数**

例如  date "+%Y-%m-%d %H:%M" 由于中间带有空格，所以使用双引号包围格式化字符串，作为整体。



## ip地址与主机名 

ifconfig 查看本机的ip地址，如无法使用ifconfig命令，可以安装：yum -y install net-tools

hostname 查看主机名

hostnamectl set-hostname 主机名，修改主机名（需root）



## --虚拟机配置固定IP



## 网络传输

ping  检查指定的网络服务器是否是可联通状态![1684230206289](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684230206289.png)

•选项：-c，检查的次数，不使用-c选项，将无限次数持续检查

•参数：ip或主机名，被检查的服务器的ip地址或主机名地址

例： ping -c 3 baidu.com 



wget 是非交互式的文件下载器，可以在命令行内下载网络文件![1684230459980](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684230459980.png)

•选项：-b，可选，后台下载，会将日志写入到当前工作目录的wget-log文件

•参数：url，下载链接



curl可以发送http网络请求，可用于：下载文件、获取信息等

•选项：-O，用于下载文件，当url是下载链接时，可以使用此选项保存文件

•参数：url，要发起请求的网络地址

curl cip.cc     cip:可以查看ip



## 端口

Linux系统是一个超大号小区，可以支持65535个端口，这6万多个端口分为3类进行使用：

端口的划分

•公认端口：1~1023，用于系统内置或常用知名软件绑定使用

•注册端口：1024~49151，用于松散绑定使用（用户自定义）

•动态端口：49152~65535，用于临时使用（多用于出口）



查看端口的占用情况    nmap命令需要安装nmap：yum -y installnmap

语法：nmap 被查看的IP地址

•22端口，一般是SSH服务使用，即FinalShell远程连接Linux所使用的端口



netstat命令，查看指定端口的占用情况

语法：netstat -anp | grep 端口号，安装netstat：yum -y installnet-tools



## 进程

ps  查看Linux系统中的进程信息 ![1684379781913](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684379781913.png)

选项：-e，显示出全部的进程

选项：-f，以完全格式化的形式展示信息（展示全部信息）

一般来说，固定用法就是： ps -ef 列出全部进程的全部信息

**从左到右分别是：**

从左到右分别是：
UID：进程所属的用户ID
PID：进程的进程号ID
PPID：进程的父ID（启动此进程的其它进程）
C：此进程的CPU占用率（百分比）
STIME：进程的启动时间
TTY：启动此进程的终端序号，如显示?，表示非终端启动
TIME：进程占用CPU的时间
CMD：进程对应的名称或启动路径或启动命令

**查看指定进程**：

ps -ef | grep tail，即可准确的找到tail命令的信息

**关闭进程**：

kill命令关闭进程 ![1684380232903](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684380232903.png)

-9，表示强制关闭进程。不使用此选项会向进程发送信号要求其关闭，但是否关闭看进程自身的处理机制。（请求关闭，进程未必会自我关闭）



## 主机状态

•top命令查看CPU、内存使用情况，类似Windows的任务管理器

​     默认每5秒刷新一次，语法：直接输入top即可，按q或ctrl + c退出

![1684380986884](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684380986884.png)



df命令，可以查看硬盘的使用情况

df [-h]

选项：-h，以更加人性化的单位显示



•iostat查看CPU、磁盘的相关信息

语法：iostat [-x] [num1] [num2]

•选项：-x，显示更多信息

•num1：数字，刷新间隔，num2：数字，刷新几次



•sar命令查看网络的相关统计（sar命令非常复杂，这里仅简单用于统计网络）

语法：sar -n DEV num1 num2

选项：-n，查看网络，DEV表示查看网络接口

num1：刷新间隔（不填就查看一次结束），num2：查看次数（不填无限次数）



## 环境变量

env：即可查看当前系统中记录的环境变量

环境变量是一种KeyValue型结构，即名称和值

无论当前工作目录是什么，都是通过PATH这个项目的值来做到的,env | grep 



$符号被用于取”变量”的值。

 比如： echo $PATH

echo ${PATH}ABC (当和其它内容混合在一起的时候，可以通过{}来标注取的变量是谁)

•临时设置，语法：export 变量名=变量值

•永久生效

•针对当前用户生效，配置在当前用户的：  iv ~/.bashrc文件中

•针对所有用户生效，配置在系统的： source  /etc/profile文件中

•并通过语法：source 配置文件，进行立刻生效，或重新登录FinalShell生效



## 上传下载

除了通过FinalShell的下方窗体进行文件的传输以外，也可以通过rz、sz命令进行文件传输。

rz、sz命令需要安装，可以通过：yum -y install lrzsz，即可安装。

rz/sz 文件名



## 压缩

![1684396033158](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684396033158.png)

常用的tar解压组合有

•tar -xvf test.tar

解压test.tar，将文件解压至当前目录

•tar -xvf test.tar -C /home/itheima

解压test.tar，将文件解压至指定目录（/home/itheima）

•tar -zxvf test.tar.gz -C /home/itheima

以Gzip模式解压test.tar.gz，将文件解压至指定目录（/home/itheima）



注意：

•-f选项，必须在选项组合体的最后一位

•-z选项，建议在开头位置

•-C选项单独使用，和解压所需的其它参数分开



使用zip命令，压缩文件为zip压缩包

语法：![1684396549731](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684396549731.png)

•-r，被压缩的包含文件夹的时候，需要使用-r选项，和rm、cp等命令的-r效果一致



unzip命令，可以方便的解压zip压缩包

语法：![1684396669108](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1684396669108.png)

•-d，指定要解压去的位置，同tar的-C选项

•参数，被解压的zip压缩包文件

•unzip test.zip -d /home/itheima，将test.zip解压到指定文件夹内（/home/itheima）







## --------------------------------

## cat 查看

查看文件内容：cat 1.txt

把多个文件合并成一个：cat 1.txt 2.txt > new.txt 原文档不会消失

创建编辑新文件：cat > 3.txt 后面接要编辑的内容，快捷键ctrl+d 或 c结束编辑(少用)

清空文件内容：cat /dev/null > 1.txt

创建新文件并编辑：cat > 4.txt <<EOF ..... EOF



## echo 输出

输出文本 echo hello     echo "hello"   echo 'hello'

-e识别特殊字符：echo -e "hello\world"

配合重定向符将内容输入到文件

">" 重定向符：表示清除源文件里面的所有内容，然后将内容加到文件的末尾

echo "new world" > 4.txt

">>"追加重定向符：直接追加内容到文件的末尾

echo "new world" > 4.txt

文件自动创建：echo "new world" > 5.txt



grep 筛选

grep 参数 模式 文件

常用参数

 -v 显示不匹配的行，也就是排除某行：grep -v new 2.txt

-n 显示匹配的行和行号：grep -n 4 2.txt （显示文件中的第4行）

-i 不区分大小写（默认是小写）：grep -i new 2.txt

-c 只统计匹配的行数：grep -c new 2.txt （有new的有几行）

-E 过滤两种不同的字符串：grep -E "new|ff" 4.txt (new和ff显出来)

--color=auto 匹配的字符串添加颜色 ？？

-w 单词为单位进行过滤：grep -w new 1.txt

-o 只输出匹配的内容：grep -o new 1.txt (只输出new)



## sed 流编辑器

sed 选项 内置命令 文件

命令

![1686214072852](C:\Users\97965\AppData\Roaming\Typora\typora-user-images\1686214072852.png)

-n 输出2，3行内容 sed -n '2,3p' 4.txt

​    过滤含有wor字符串的行并显示 （与grep不同需要双斜线包含字符串）：sed -n '/new/p' 4.txt

​    删除new并显示不会删除源文件     sed '/new/d' 4.txt 

-i 删除指定行 sed -i '2d' 4.txt(删除第2行) 、

​                        sed - i '2,4d' 4.txt (删除2-4行)

g 全局替换：sed 's#new#old#g' 4.txt 将所有的new替换成old临时替换并显示不会修改源文件，

​                                       如果需要修改添加 -i

-e 多项编辑 ：sed -e 's#new#old#g' -e ''s#123#456#g' 4.txt (new替换成old,并123替换成456）

a 追加：sed '2a hello' 4.txt (在第二行临时追加显示 hello，不同行用 \n 隔开 \)

sed -i '2i test' 4.txt 在第二行中插入文本不临时的

## awk

awk [参数] '条件{动作}' file...

参数

