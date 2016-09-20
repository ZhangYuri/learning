##Hybrid App开发的基本步骤
###一、安装
####1.安装node.js

####2.安装git

####3.安装ionic & cordova：
  命令行输入：

    npm install –g cordova ionic
  **注：**-g表示全局安装
####4.安装Java JDK（Mac自带，不需安装）

####5.安装Apache Ant

####6.安装Android SDK（从这里开始后面基本以android为例，ios类似）

####7.设置环境变量：
  
  ①打开计算机->系统属性->高级系统设置->环境变量
  
  ②在系统变量中新建`ANDROID_HOME`变量，变量值为sdk所在目录，如图
  
  ③新建`CLASSPATH`变量，变量值为
  
    .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
  
  ④新建`JAVA_HOME`变量，变量值为`jdk`所在目录
  
  ⑤编辑系统变量中的`path`变量，不要删原来的变量值，在原值后面添加   
 
    ;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;%ANDROID_HOME%\tools;%ANDROID_HOME%\build-tools;%ANDROID_HOME%\platform-tools 

**注：**这里是添加了jdk\bin、jdk\jre\bin、sdk\tools 、sdk\build-tools、sdk\platform-tools的路径，互相以英文分号隔开

####8.创建项目：
进入想要存放app的目录，命令行执行： 
  
    ionic start `AppName` blank，
**说明：**`AppName`为项目文件夹的名字，可自定义，并在里面初始化一个ionic项目。
####9.添加平台
  进入刚才新建的项目的目录，命令行输入
     
     ionic platform add android


###二、测试项目
####1.进入项目目录，编译项目
    ionic build android

####2.测试项目的方法：
    
#####1).桌面浏览器测试法：
    ionic serve
    
#####2).模拟器测试法：
    ionic emulate android
   
#####3).真机测试法：连上数据线，打开开发者选项，执行
  
    ionic run android
    
**注：**必须确保电脑上安装了正确的驱动，使用如下指令，若显示所连接的设备，则驱动安装正确

    adb devices

**tip:**使用chrome浏览器自带的远程调试：打开chrome浏览器，在地址栏输入 
`chrome://inspect/#devices`，然后勾选上`Discover USB devices`，便可以看到你的设备



###三、编写项目
参考：<http://ionicframework.com/docs/guide/building.html> 

###四、打包app
####1.准备工作，执行：
    cordova plugin rm cordova-plugin-console

####2.生成未签名的包：
    cordova build --release android
在`platforms/android/build/outputs/apk`，中会出现`android-release-unsigned.apk`

####3.使用keytool生成证书
#####1).转至要运行证书的目录
#####2).输入以下命令生成证书
    keytool -genkey -alias keyAlias
    -keyalg RSA 
    -keypass keyPassword
    -storepass storePassword
    -keystore name.keystore
**说明：**keyAlias:证书别名；keyPassword：私钥密码；storePassword：密钥库密码；name.keystore:证书名，以.keystore作为后缀名。
#####3).删除证书
    keytool -delete
    -alias keyAlias
    -keystore keystore-name
    -storepass password
#####4).导出证书
    keytool -export -alias keyAlias
    -storepass storePassword
    -file server.cer
    -keystore name.keystore
**说明：**server.cer:将证书导出为server.cer,也可以是别的名字。
#####5).获取所有命令
    keytool -help


####4.给未签名的apk签名：

    jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore HelloWorld-release-unsigned.apk alias_name

####5.最后一步
    zipalign -v 4 HelloWorld-release-unsigned.apk HelloWorld.apk


###五、参考网址：
<http://ionicframework.com/docs/guide/preface.html>
<https://cordova.apache.org/docs/en/latest/guide/cli/index.html#link-3>
<http://developer.android.com/sdk/installing/adding-packages.html>
<https://developer.apple.com/ios/download/>
