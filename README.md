# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下


```
parsers: # array
- reg: ^.*$     ## 匹配所有订阅
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule2,DIRECT   # 不用走代理的一些网站
    mix-rule-providers:
      jxhrule2: # 不需代理的常见软件列表
        type: http
        behavior: classical
        url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoDirect.yaml"
        path: ./ruleset/jxhrule2.yaml
        interval: 86400               

# 某一订阅走法调整 
- url: <--复制粘贴--> 
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule,<--复制黏贴-->  # 第三个元素需要按自己订阅修改
    mix-rule-providers:
      jxhrule: # 需要代理的常见软件列表
        type: http
        behavior: classical
        url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoThroughProxy0.yaml"
        # url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules@main/GoThroughProxy0.yaml"
        path: ./ruleset/jxhrule.yaml
        interval: 86400       
```

## 设置--系统代理--绕过域设置添加下列

因为clash即使直连延迟也不如不开代理时，或者使用PAC模式

```
bypass:
  - "bilibili.com" # 哔哩哔哩
  - "baidu.com" # 百度
  - "csdn.net" # CSDN
  - "zhihu.com" # 知乎
  - "alicdn.com" # 阿里转发
  - "qq.com" # 腾讯相关软件
```

## 评价
- [星梦数据机场](https://stardream.xyz/user)☆，8r/月
- [魔戒机场](https://www.mojie.cyou/)☆☆，0.1r/1G
- [nano机场](https://v3.nanoport.xyz/#/dashboard)，目前在试大盘鸡套餐



## Issues
`clash客户端长时间开启后故障，大部分按钮点击后没有效果 `

最后发现是杀毒软件的问题，卸载并更换杀毒软件可以解决
