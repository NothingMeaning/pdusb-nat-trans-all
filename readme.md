
# Arm Aarch64 各种NAT穿越包合集

![加速](https://gitee.com/pdusb/pdusb-nat-trans-all/raw/master/imgs/pdbolt-nat-trans-all-in-one.jpg)

# 这是个啥
- 八种NAT穿越常用包汇总
- 提供deb/rpm/tarball等三种格式,方便在不同的系统上安装
- 支持Arm64 CPU,尚未支持Arm32以及x86等
- 提供对应软件的systemd服务文件
- 各软件log归一到同一目录的不同文件,便于调试

对应的NAT穿越软件均从其各自官网下载，因NAT穿越的包大部分为静态链接的二进制文件，不存在编译和修改的情况


# 各NAT穿越包详情

| 名称     | 可执行文件路径 | 配置文件 | 服务脚本文件 | Log 文件路径 |  说明 |
| ----------- | ----------- | ------ | ----------- |  ----- |  --- | 
| 网云穿   | /usr/local/pdboltnat/wyc/wyc     |  没有 | /lib/systemd/system/wyc@.service | /var/log/pdboltnat/wyc.txt |  |
| 神卓互联 | /usr/local/pdboltnat/shenzhuo/shenzhuo     |  没有 | /lib/systemd/system/shenzhuo.service | /var/log/pdboltnat/shenzhuo.txt | |
| Sakurafrp | /usr/local/pdboltnat/sakurafrp/natfrpc     |  没有 | /lib/systemd/system/natfrp@.service | /var/log/pdboltnat/natfrp.txt | |
| 花生壳 | /usr/local/pdboltnat/oray/phddns     |  没有 | /lib/systemd/system/oray.service | /var/log/pdboltnat/oray.txt | |
| FRP | /usr/local/pdboltnat/frp/frpc     | /etc/frp/frpc.ini | /lib/systemd/system/frpc.service | /var/log/pdboltnat/frpc.txt | |
| ddnsto | /usr/local/pdboltnat/ddnsto/ddnsto     | 没有 | /lib/systemd/system/ddnsto@.service | /var/log/pdboltnat/ddnsto.txt | |
| 蜻蜓映射 | /usr/local/pdboltnat/flynat/flynatc     | 没有 | /lib/systemd/system/flynat.service | /var/log/pdboltnat/flynat.txt | |
| ZeroTier | /usr/local/pdboltnat/zerotier/zerotier-cli     | 没有 | 还没有 | /var/log/pdboltnat/zerotier.txt | |

# 使用方法

## 安装包
### Debian类
  下载包到系统
  - 方法1
  dpkg -i ./

  - 方法2
  apt-get install ./

### RPM包
  

### tar包

直接解压即可


## 网云穿
[官网帮助文件](http://www.neiwangchuantou.cn/archives/30.html)

只是需要从控制面板记录下自己的令牌即可

```Bash
systemctl enable wyc@这几个字符替换为你实际的令牌.service
systemctl start wyc@这几个字符替换为你实际的令牌.service
```



## 神卓互联
[官网帮助页面](https://www.shenzhuohl.com/article/1/shenzhuo/show/49)

只需要看下如何获取用户名和密码即可


- 编辑服务文件
```Bash
  cd /lib/systemd/system
  vi shenzhuo.service
  # 把下面一行中的用户名和密码替换为你实际的
  ExecStart=/usr/local/pdboltnat/shenzhuo/shenzhuo 换成你的用户名 换成你的密码
```
- 开启服务
  systemctl enable shenzhuo.service
  systemctl start shenzhuo.service

## Sakurafrp NATFRP

[官网帮助页面](https://doc.natfrp.com/#/frpc/manual)

只看如何获取token和隧道即可

- 开启服务
  systemctl enable natfrap@你的TOKEN:隧道呀.service
  systemctl start natfrap@你的TOKEN:隧道呀.service

## 花生壳

[官网帮助页面](https://service.oray.com/question/11630.html)

还在调试中

## FRP
[官网帮助页面](https://github.com/fatedier/frp)

## DDNSTO
[官网帮助页面](https://www.ddnsto.com/zh/guide/koolshare_merlin.html)


- 开启服务
  systemctl enable ddnsto@你的TOKEN.service
  systemctl start ddnsto@你的TOKEN.service

## 蜻蜓映射
[官网帮助页面](https://flynat.51miaole.com/docs/start/commands/)

- 编辑服务文件
```Bash
  cd /lib/systemd/system
  vi flynat.service
  # 把下面一行中的用户名和token替换为你实际的
  ExecStart=/usr/local/pdboltnat/flynat/flynatc -u 你的用户名 -k 你的token
```

- 开启服务
  systemctl enable flynat.service
  systemctl start flynat.service

## 交流沟通

愉快的加入QQ群聊吧

![群聊](https://gitee.com/pdusb/pdusb-fast-btpanel/raw/master/imgs/pdbolt-conn-qq-group.jpeg)


