- `注意:V2ray的使用需要保证VPS服务器和你使用的客户端之间的时差小于2分钟,因此从调整时间开始(默认中国大陆上海时间)`

- `建议使用 Debian 9 系统,其它系统不建议使用,可能会遇见 Common not found 报错`

`cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`   修改VPS时间

`date -R`  查看时间,确保时差小于2分钟

`bash <(curl -L -s https://install.direct/go.sh)`  安装脚本

`vim /etc/v2ray/config.json`  修改配置文件 **`(需要删除原有全部配置信息,并复制新生成的配置文件)`**

在这个[网站](https://intmainreturn0.com/v2ray-config-gen/#) 生成V2ray配置文件:

1.服务种类: Vmess

2.用户设置: `用户uuid`旁点击`重新生成`,`使用的alterID数量`建议输入100~200内的数,可有效降低VPS服务器运算压力

3.`端口号`和`动态端口范围`根据网站要求填写

4.*注意:网站上默认勾选的请不要取消,否则可能降低代理速度*

**为防止生成配置文件的网站不可使用,作为备用方案的本地配置文件生成器已上传,点击[这里](https://github.com/charlieethan/V2ray-install/releases/download/V2.0/V2RayConfig.zip)下载**

`:wq`  保存并退出
`service v2ray restart`  重启V2ray服务
`service v2ray status`  检查V2ray运行情况,若显示**Active**则运行正常

- 本地客户端配置:
建议Windows使用GUI版本:[V2rayN](https://github.com/charlieethan/V2ray-install/releases/download/V1.0/v2rayN.zip)(点击下载)Android使用Google应用商店的`V2rayNG`.原项目地址点击[这里](https://github.com/2dust/v2rayN/releases)
1.添加Vmess服务器

2.*地址*为服务器IP,*用户ID* 为刚才生成的`用户uuid`,*额外ID* 为`使用的alterID数量`中填写的数字,*加密方式*随意,*传输协议*选择**Kcp**

3.*别名*以下的部分不知道就不填

4.电脑托盘中点击右键并选择*启用Http代理* 测试网络连接
