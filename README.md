# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下

```
parsers: # array
# - reg: ^.*$ 匹配所有订阅，或  - url: https://stardream.pw/link/gKq9gq2kn53bCavu?clash=1 指定订阅
- reg: ^.*$
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule,魔戒.net  # 第三个元素需要按自己订阅修改
    mix-rule-providers:
      jxhrule: # 需要代理的常见软件列表
        type: http
        behavior: classical
        # url: "https://raw.githubusercontent.com/huakyouin/clash-rules/main/GoThroughProxy0.yaml"
        url: "https://cdn.jsdelivr.net/gh/huakyouin/clash-rules/main/GoThroughProxy0.yaml"
        path: ./ruleset/jxhrule.yaml
        interval: 240
```

## clash Home文件夹下config.yaml添加下述防止DNS污染
```
dns:
  enable: true
  nameserver:
    - https://dns.alidns.com/dns-query
  # 提供 fallback 时，如果GEOIP非 CN 中国时使用 fallback 解析
  fallback:
    - 1.1.1.1 # cloudflare DNS UDP
    - 8.8.8.8 # Google DNS UDP
    # 强制DNS解析使用`fallback`配置
  fallback-filter:
    # true: CN使用nameserver解析，非CN使用fallback
    geoip: true
    # geoip设置为false时有效： 不匹配`ipcidr`地址时会使用`nameserver`结果，匹配`ipcidr`地址时使用`fallback`结果。
    ipcidr:
      - 240.0.0.0/4
```
