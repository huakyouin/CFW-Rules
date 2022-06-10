# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下

Note：星梦数据机场适用

```
parsers: # array
# - reg: ^.*$ 匹配所有订阅，或  - url: https://stardream.pw/link/gKq9gq2kn53bCavu?clash=1 指定订阅
- reg: ^.*$
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule,魔戒.net  # 第三个元素需要按自己订阅修改
      - RULE-SET,jxhrule2,DIRECT   # 不用走代理的一些网站
    mix-rule-providers:
      jxhrule: # 需要代理的常见软件列表
        type: http
        behavior: classical
        url: "https://raw.githubusercontent.com/huakyouin/clash-rules/main/GoThroughProxy0.yaml"
        # url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules/main/GoThroughProxy0.yaml"
        path: ./ruleset/jxhrule.yaml
        interval: 86400
      jxhrule2: # 不需代理的常见软件列表
        type: http
        behavior: classical
        url: "https://raw.githubusercontent.com/huakyouin/clash-rules/main/GoDirect.yaml"
        path: ./ruleset/jxhrule2.yaml
        interval: 86400
```

## 评价
- 星梦数据机场涨价了，8r/月，在自定义规则后表现尚可，但我没续费了
- 魔戒机场按量计价量大管饱0.1r/1G，但是配置文件冲突严重，导致我clash和v2ray核心频繁熄火，无法电脑长期开启，备选
- 现在在用翻墙机场，3r/月，待评价
