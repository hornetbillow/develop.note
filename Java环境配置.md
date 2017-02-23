# 配置Java开发环境笔记
*描述信息*

## 安装JDK和Tomcat
- 安装JDK：直接运行jdk-7-windows-i586.exe可执行程序，默认安装即可。
备注：路径可以其他盘符，不建议路径包含中文名及特殊符号。
- 安装Tomcat：直接解压缩下载文件“apache-tomcat-7.0.33-windows-x86.zip”到C盘下。安装路径建议修改为：c:\tomcat。
- *备注：如下载的是可执行文件，双击运行，默认安装即可。*

## 配置JDK环境变量
1. 新建变量名称：JAVA_HOME,变量值：C:\Program Files\Java\jdk1.7.0
2. 打开path，添加变量值 `%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`
3. 新建变量名：CLASSPATH,变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar

#### 备注信息：
- .表示当前路径，%JAVA_HOME%就是引用前面指定的JAVA_HOME；
- JAVA_HOME指明JDK安装路径，此路径下包括lib，bin，jre等文件夹，tomcat，eclipse等的运行都需要依靠此变量。
- PATH使得系统可以在任何路径下识别java命令。
- CLASSPATH为java加载类(class or lib)路径，只有类在classpath中，java命令才能识别。

#### 测试JDK
*在CMD命令下输入javac，java，javadoc命令：出现图示界面，表示安装成功*

## 配置Tomcat环境变量
- 新建变量名：CATALINA_BASE，变量值：C:\tomcat
- 新建变量名：CATALINA_HOME，变量值：C:\tomcat
- 打开PATH，添加变量值：%CATALINA_HOME%\lib;%CATALINA_HOME%\bin

## 如何启动Tomcat服务
*方法有两种*

- 方法一 在CMD命令下输入命令：startup,出现启动服务的对话框，表明服务启动成功
- 方法二 右键点击桌面上的"我的电脑" -> "管理" -> "服务和应用程序" -> "服务"，找到"Apache Tomcat" 服务，右键点击该服务，选择"属性",
将"启动类型" 由 "手动" 改为 "自动" 

## 测试Tomcat

- 打开浏览器，在地址栏中输入"http://localhost:8080" 回车，如果看到Tomcat 自带的一个JSP页面，说明你的JDK和Tomcat已经搭建成功。


## **注意事项：**
1. JAVA_HOME中的路径不能用分号结尾，如C:\Program Files\Java\jdk1.7.0。
2. CATALINA_BASE，CATALINA_HOME，TOMCAT_HOME中的路径不能以“\”结尾。
3. JAVA_HOME的路径一定不要写成了JRE的路径。
4. 在环境变量中修改添加变量时，一定要注意分号、空格，是否有多余的字母。作者就是因为path路径中多了一个字母，怎么都配置不成功。如果配置不成功，一定要反复检查。
   以上错误，非常容易出现错误：CATALINA_HOME或是JAVA_HOME没有配置好。如错误提示“The CATALINA_HOME environment variable is not defined correctly”
