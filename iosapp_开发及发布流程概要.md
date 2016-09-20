##iosApp 开发及发布流程概要
###一、App瘦身
####1.Slicing(ios,tvos)
####2.Bitcode
####3.On-Demand Resource(ios,tvos)
###二、配置准备提交的Xcode项目
####1.在创建时设置属性
####2.配置ID和团队设置
1）设置bundle ID前缀：com.Lekeopen.tsflea

2）设置bundle ID

3）分配项目给团队
####3.设置部署信息
1）设置部署的目标

2）设置目标设备
####4.添加图标和启动动画
####5.验证build设置

###三、在模拟设备上运行app
###四、导出要测试的app
####1.注册测试设备
####2.将app存档
####3.导出.ipa便于真机测试
####4.安装到测试机
####5.复制App沙盒数据
####6.从Tester获取Crash报告
###五、上传app到iTunes Connect
####1.在iTunes Connect上创建App记录
####2.更新版本和Build Strings
####3.将app存档
1）检查存档计划设置

2）创建存档
####4.运行iTunes Connect Validation Tests
####5.上传App

###六、使用TestFlight发布app
###七、分析Crash报告
###八、提交app到App Store
####1.提交的App的准备工作
1）检查用户界面和存储指导方针

2）在iTuneConnect上输入其他信息

3）验证Xcode项目
####2.上传最终版本
####3.提交APP到App Store

###九、在iTunesConnect管理App
###十、参考网站
<https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012582-CH1-SW1>