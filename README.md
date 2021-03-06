## NIHAO

![py](https://img.shields.io/badge/python-3.6.1-red.svg?style=plastic)  ![plat](https://img.shields.io/badge/platform-Ubuntu16.04-red.svg?style=plastic)

---

>NIHAO 实现了在Linux下的多人聊天系统

1. 架构模式

   1. 采用 `CS` 模式的架构
   2. 服务器任务
      * 识别用户的登录请求 : 登录的时候需要提交用户的一些基础数据,登录之前都是客户端和服务器之间的交互，但是登陆之后有可能是用户和用户，也有可能是用户和服务器
        1. 用户的 `IP` 地址
        2. 用户的身份信息
      * 用户的 `IP` 地址确定和身份绑定
      * 在线成员的信息归档登记
      * BBS信息处理
      * 自然语言扩展模块的处理或者是将自然语言扩展模块执行权限分发给用户
      * 将两个用户聊天的 `Socket` 转接，不用经过服务器，节省服务器的资源
      * 数据信息的存储
   3. 客户端任务
      * 多人通讯等主要的功能
      * 本地信息的存储(文件存储，在服务器上进行备份)

2. 仓库组成

   * 及时通讯

     1. 多进程多终端及时通讯
        * 单用户 - 单用户
        * 多用户 - 多用户
        * 单用户 - 机器 (用户或者服务器)

     2. 文件发送，图片发送，音频发送(**text中加入**)

        对服务器的文件发送视为向 BBS 的 Upload

   * BBS

     1. **功能** : 下载，上传数据，公告推送阅读
     2. 每一个用户存在有传输文件大小限制(总限制大小)

   * 数据存储 - MySQL,客户端本地的二进制保存文件

     1. 用户信息存储
     2. 历史记录存储 : 存在容量限制
     3. BBS论坛公共数据存储

   * 完整实现
     1. 基础模块

        * 界面模块 : 最好可以支持 `Temux` 的终端模拟软件的使用

          1. Tkinter
          2. PyQT

          **GUI-GUI, GUI-Terminal, Termial-Terminal, 本质上是对及时通信模块的封装**

          1. GUI
          2. Terminal

        * 用户模块(用户信息存储，用户登录)

     2. 扩展模块(`tensorflow` 训练实践，最后考虑)
        * 人脸识别登录(人工智能自我实践项目)
        * 自然语言处理 (后期的兴趣项目) 

   * 部署模块

     1. 不能像以前的代码一样，需要对仓库的代码文件进行有效的部署
     2. 部署采用 `shell` 脚本执行
     3. **强调一键安装的便利性**
     4. 部署强调对于软件需要的依赖包的管理和**自动下载策略**
     5. 部署分为两个模块 
        * 服务器部署
        * 客户端部署

3. 客户端逻辑组织

   1. 界面模块调用显示
   2. 通信模块包含
   3. 数据存储模块包含
   4. 扩展模块包含
   5. 用户模块

4. 服务端逻辑组织 : **服务器启动的时候返回当前的 `IP` 地址**

   1. BBS
   2. 通信模块
   3. 界面模块只需要 Terminal 界面即可
   4. 扩展模块
   5. MySQL模块

5. 环境

   * `Python 3.6+`
   * `bash`
   * `Ubuntu 16.04+`
   * `tensorflow 1.4+`

6. 扩展模块记录
   1. 计算机视觉
      * 人脸识别登录
   2. 自然语言处理
      * 自动问答回复
      * 写诗等等
      * 可以考虑对 `Asimov` 的 API 调用回复更多有趣的文本
