# lx-step
【Python】腾讯云云函数配合乐心健康刷QQ、微信、支付宝步数(支持随机步数、微信QQ推送)

# 说在前面
乐心健康规定要绑定手环等智能设备才可以将数据推送到第三方，此次更新只解决了接口问题，实测可以完成刷步，但是由于本人身边没有手环这种智能设备，数据同步第三方应用是否可行未进行测试，理论上是乐心新规定的问题。

下面是测试截图：
![QQ截图20201029224207.png](https://i.loli.net/2020/10/29/iB8QvXl4HnudS7J.png)
![Screenshot_20201029_223528_gz.lifesense.weidong.jpg](https://i.loli.net/2020/10/29/dcm2KpuNXMjFDSB.jpg)
![Screenshot_20201029_222324_gz.lifesense.weidong.jpg](https://i.loli.net/2020/10/29/N7fgmeXyYO5WkRI.jpg)

# 方法
1. 下载乐心健康APP：官方下载地址：http://www.lifesense.com/app/
2. 从应用商店下载乐心健康App，打开软件并选择手机号登录
3. 登录之后，点击我的->设置->账号与安全->设置密码(修改密码)，设置你自己记得住的密码
4. 回到App首页，点击我的->数据共享，绑定你想同步数据的项目注：同步微信运动请按照要求关注【乐心运动】公众号。
5. 回到云函数代码，配置好下图参数，运行即可提交步数即可同步至你绑定的所有平台
![1](https://attach.52pojie.cn/forum/202009/26/220610s1ehd59u55uh5uce.png)
6. 设置好云函数触发规则

# 其他
[https://www.52pojie.cn/thread-1274977-1-1.html](https://www.52pojie.cn/thread-1274977-1-1.html)
