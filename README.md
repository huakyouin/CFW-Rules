# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下


```
parsers: # array
# - reg: ^.*$ # 匹配所有订阅
- url: https://gfwairport.icu/api/v1/client/subscribe?token=905e00df92af82e5937c0af157f6e95b # 自己订阅的网址
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule,翻墙机场  # 第三个元素需要按自己订阅修改
      - RULE-SET,jxhrule2,DIRECT   # 不用走代理的一些网站
    mix-rule-providers:
      jxhrule: # 需要代理的常见软件列表
        type: http
        behavior: classical
        url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoThroughProxy0.yaml"
        # url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoThroughProxy0.yaml"
        path: ./ruleset/jxhrule.yaml
        interval: 86400
      jxhrule2: # 不需代理的常见软件列表
        type: http
        behavior: classical
        url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoDirect.yaml"
        path: ./ruleset/jxhrule2.yaml
        interval: 86400
    commands:
      - dns.enable=false                      # 不使用订阅中的dns 防止时不时断开
      - external-controller=127.0.0.1:12339     # 按自己的core端口调整
```

## 设置--系统代理--绕过域设置如下

因为clash即使直连延迟也不如不开代理时
```
bypass:
  - localhost
  - 127.*
  - 10.*
  - 172.16.*
  - 172.17.*
  - 172.18.*
  - 172.19.*
  - 172.20.*
  - 172.21.*
  - 172.22.*
  - 172.23.*
  - 172.24.*
  - 172.25.*
  - 172.26.*
  - 172.27.*
  - 172.28.*
  - 172.29.*
  - 172.30.*
  - 172.31.*
  - 192.168.*
  - <local>
  - "bilibili.com" # 哔哩哔哩
  - "baidu.com" # 百度
  - "csdn.net" # CSDN
  - "zhihu.com" # 知乎
  - "alicdn.com" # 阿里转发
  - "qq.com" # 腾讯相关软件
```

## 评价
- [星梦数据机场](https://stardream.xyz/user)涨价了，8r/月，在自定义规则后表现尚可，但我没续费了
- [魔戒机场](https://www.mojie.cyou/)按量计价量大管饱，0.1r/1G，但是不太稳定
- [翻墙机场](https://xn--mest5a943ag8x.net/#/knowledge)目前在用，3r/月，目前还不错



