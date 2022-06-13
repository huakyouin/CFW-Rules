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
- [星梦数据机场](https://stardream.xyz/user)涨价了，8r/月，在自定义规则后表现尚可，但我没续费了
- [魔戒机场](https://www.mojie.cyou/)按量计价量大管饱，0.1r/1G，但是不太稳定
- [翻墙机场](https://xn--mest5a943ag8x.net/#/knowledge)目前在用，3r/月，目前还不错

## Issue
我遇到了这样的问题：clash启动一会后随着某个联网需求产生，突然失去与clash core的链接

目前已尝试：

### 1. 降级核心【无效】

参考[这篇文章](https://matters.news/@looklookworld/57425-%E6%9C%80%E8%AF%A6%E7%BB%86clash-r%E6%95%99%E7%A8%8B-clash-x%E6%95%99%E7%A8%8B-clash-a-clash-web-pharos-pro-%E5%A4%9A%E5%B9%B3%E5%8F%B0%E7%89%88%E6%9C%AC-bafyreibrj4m6z6ttojc3yqiurz767wlphrkqkoymvpldtx2rzsm6tse7uy)

### 2. 重置电脑与路由器一些可以安全修改的网络设置【无效】

客户端左侧`setting`->`system proxy`(系统代理)->第二行`绕过域/网络`点击`edit`，按下面格式添加日志中timeout网站的域名或ip

```
bypass:
  - localhost
  - 127.*
  - 127.0.0.1
  # 国内常见直接绕过
  - "bilibili.com" # 哔哩哔哩
  - "baidu.com" # 百度
  - "csdn.net" # CSDN
  - "zhihu.com" # 知乎
  - "alicdn.com" # 阿里转发
  - "weixin.qq.com" # 微信客户端
```

右键windows图标以管理员打开终端输入`netsh winsock reset`，然后重启电脑和路由器

### 3. 给客户端网络权限【无效】

任务浏览器里找到CFW的exe文件和clash-win64.exe打开路径，右键兼容性勾选管理员启动

### 4. 防火墙检查【待验证】

`xindows键`->搜索`控制面板`->`系统和安全`->`Windows Defender防火墙`->左侧`高级设置`->`入站规则`->检查clash相关权限



