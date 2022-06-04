# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下

```
parsers: # array
# - reg: ^.*$ 匹配所有订阅，或  - url: https://stardream.pw/link/gKq9gq2kn53bCavu?clash=1 指定订阅
- reg: ^.*$
  yaml:
    prepend-rules:
      - RULE-SET,MyRules,魔戒.net   # 魔戒.net、🔰国外流量等是我订阅源中的代理分组名字
    mix-rule-providers:
      mine: # 需要代理的常见软件列表
        type: http
        behavior: classical
        url: "https://raw.githubusercontent.com/huakyouin/clash-rules/main/GoThroughProxy0.yaml"
        path: ./MyRules.yaml
        interval: 240
