# clash-rules
自用clash规则


## 订阅源右键parser设置修改成如下


```
parsers: # array
# - reg: ^.*$ # 匹配所有订阅
# 自己订阅的网址
- url: https://subv2.nanoport.xyz/api/v1/client/subscribe?token=bd6477706f3d605e176258d51788c715 
  code: |
    module.exports.parse = async (raw, { axios, yaml, notify, console }, { name, url, interval, selected }) => {
      const obj = yaml.parse(raw)
      obj.proxies.forEach( v => {
          if (v.network === 'ws' && !v['ws-opts'] && v['ws-path'] && !v['ws-headers']) {
            const opts = {}
            opts.path = v['ws-path']
            v['ws-opts'] = opts
            delete v['ws-path']
          }
          if (v.network === 'ws' && !v['ws-opts'] && v['ws-path'] && v['ws-headers']) {
            const opts = {}
            opts.path = v['ws-path']
            opts.headers = v['ws-headers']
            v['ws-opts'] = opts
            delete v['ws-path']
            delete v['ws-headers']
          }
      })
      return yaml.stringify(obj)
    }
  yaml:
    prepend-rules:
      - RULE-SET,jxhrule,nanoPort  # 第三个元素需要按自己订阅修改
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
      - mixed-port=12336
      - dns.enable=false                      # 不使用订阅中的dns 防止时不时断开
      - external-controller=127.0.0.1:12339     # 按自己的core端口调整
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



