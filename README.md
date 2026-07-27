# Proxy App List

> A curated list of proxy clients for all platforms, updated to 2026-05-15.
> 
> Original source: https://www.haitunt.org/app.html

# 代理工具箱

由于市井流传的 App 清单大多停留在 Clash 删库前 (2023.10) 的软件生态，本篇另起炉灶，旨在梳理一份“与时俱进”的清单，涵盖移动端、电脑端、硬路由、软路由等平台，以及规则集、小工具、订阅转换等周边产品。

若有新软件或既有信息失去时效，欢迎前往[电报 @HaitunSubmit_bot](tg://user?id=8157739759) 或 [@haitun_channel](https://t.me/haitun_channel) 举荐、反馈。

不同底色标签之义: 备注 备注2 价值信息 简评 挑刺 风险

**最近 update**: 2026-05-15, 新增 MonadBox (🤖)、Anywhere (🍎)、MConnect (🧿🤖)、XrayUI (🪟)、Singboard for Mac (🍏).

**Last update**: 2026-04-17, 新增 Carton (🪟🐧)、Nextin (🍎)；🔄 订阅转换 删去过时域名，增加 subboost.org；对照 YumeBox、Surfboard 等 Apps 的进展修改描述；调整 iOS 的分类排序，不再与 tvOS 的支持度捆绑（今时今日这么用它的人已不多）

## 📚 代理方案优先序 An Roadmap

### 基础需求

#### 对应“流动场所➕单设备”的使用场景，参照终端设备及操作系统进行选择。

### 甜点需求

#### 对应“固定场所➕长时间开启➕≥2台设备”的使用场景，愿花一下午时间研究，但认为：易用性＞极致体验

> 🛜 华硕 路由器 ＋
- [代理插件](#asus)
★★★ ￥400～2000元预算 对于绝大部分人而言，它接近“功能性✖️易用性✖️预算”的最佳平衡点：刷固件、装插件属于“有手就会” WiFi 6及之后机型都够跑满⚡≥1.5G的*单线程*代理 可扩展Samba、多种内网穿透、DDNS、OpenList、Node.js、RustDesk Server，等等 插件仅能安装到[官改/梅林固件](https://www.asusgo.com/firmware)
路由器售价比小米/红米稍贵，但插件免费 中低端机型的ROM 256MB，若不插入U盘扩容，能装下的插件数量有限 > 🍏 Mac Mini ＋
- [Surge/Stash for Mac](#macrouter)
★★☆ ￥3000元预算 作旁路网关使用。通用iOS版配置文件，提供GUI的Dashboard对新手更友好 国补后 Mac Mini (M4 万兆版) 本身也属*最便宜*万兆软路由 更昂贵的方案，但投入-回报率极低：开启代理后的网络实际体感，相对 华硕/小米硬路由 基本拉不开差距 仅支持fake-ip，搭配游戏加速器、局域网备份、投屏等App时易导致奇奇怪怪的问题 基于MitM去广告等功能或导致局域网内⛔不信任用户自签证书的*非苹果*设备⛔加载网页出错，仅适合苹果设备only的家庭！ > 🛜 小米/红米 路由器 ＋
- [代理插件](#xiaomi)
★★ ￥120～1000元预算 物美价廉，各档机型丰俭由君 多数 WiFi 6 及之后机型，CPU都够跑满千兆*单线程*代理（但搭载MT7981的AX3000T/WR30U等机型除外） 安装插件必须先解锁SSH，且操作比华硕、Apple TV稍显繁琐 中低端机型的ROM仅128MB，官方固件下的存储空间仅够装 ShellCrash 不刷OpenWrt的话，扩展性也不如华硕和Apple TV > 🍎 Apple TV (有线) ＋
- [一类/二类 Apps](#ios)
★ ￥1000元预算 作旁路网关使用。通用iOS代理App及其配置文件 稳定性不如前三者，是个别博主的“你用他推荐，但私下他不用”的非主流方案 tvOS对代理类app运存限制15MB（远低于iOS的50MB），使MitM等脚本非常局促 扩展性不如华硕、刷OpenWrt的小米 若非电视刚需，不值得为醋包饺子 仅支持fake-ip，搭配游戏加速器、局域网备份、投屏等App时易导致奇奇怪怪的问题 基于MitM去广告等功能或导致局域网内⛔不信任用户自签证书的*非苹果*设备⛔加载网页出错，仅适合苹果设备only的家庭！

#### 注：二星 ★★ 及以上都足以覆盖 90% 的群体

### 进阶需求

#### 若追求更极致、更客制化的体验，可能还包括：

> 远距离的单线程 ≥1000Mbps 仅武汉、合肥等极少数“三边形城市”可以忽略该问题 类Unix默认参数下，广东/西南/西北/东北…跑不满🇯🇵🇺🇸沪日，江苏/河南/华北/西南…跑不满🇭🇰🇸🇬粤港，湖南/华南/西南/西北…跑不满🇪🇺🇩🇪京欧 刚需 OpenWrt/Linux 进行[TCP调优（打鸡血）](https://t.me/haitun_channel/840)，否则距入口＞约25ms的*远距单线程*可能卡在～650Mbps瓶颈——技术性资料见[谷歌云Google Cloud](https://cloud.google.com/compute/docs/networking/tcp-optimization-for-network-performance-in-gcp-and-hybrid?hl=zh-cn)
> 较挑剔的 国内➕国外 双重极致体感 国内、国外的极致延迟在Surge/Mihomo/Stash下两难全，即便以fake-ip为代价也只能“二者取其一” 刚需 Sing-box 核心 或[爱快/ROS的“伪多拨回环分流”](https://www.youtube.com/watch?v=3B1MSVF43o4)
> 适配 多拨/宽带聚合 的分流代理 > 不管能否派上用场，所有性能指标我都要*最极致*！ > 其他客制化需求……

## 📱 移动端 Mobile Devices

### 🤖 Android 安卓

#### 一类

>
- [Exclave](https://github.com/dyhkwong/Exclave)
～自建党/单节点梭哈 基于v2ray核心，稳定、简单易用、链式代理易操作 🟢新协议、新特性都迅速跟进，协议覆盖率《全平台第一》！ 分流繁琐；UI走经典的Material Design公模风 >
- [FlClash](https://github.com/chen08209/FlClash)
全协议支持、分流、相对省电、异常勤快的更新频率，对Meta写法的配置文件可视化适配极佳 仿 Surfboard UI（但功能上青出于蓝），覆写可选项比CMFA少 >
- [Clash Meta for Android](https://github.com/MetaCubeX/ClashMetaForAndroid)
(CMFA) 全协议支持、分流、更新积极、覆写可选项全、MetaCubeX/Mihomo官方分支 UI一般/交互逻辑不太合乎直觉，对带icon的proxy-group及rule-providers等Meta写法的配置文件可视化效果一般 >
- [Sing-box for Android](https://sing-box.sagernet.org/zh/clients/android/)
全协议支持、分流、最强DNS处理、省电优化好、衔接Tailscale内网穿透、更新积极、免费，迭代激进/屎山代码风险小，基本能做到一个配置文件通杀《全平台》 GUI极其简陋、学习曲线陡峭；配置难度高/覆写全靠手搓config.json；迭代激进/旧配置文件可能跨版本不兼容

#### 二类

>
- [Husi](https://codeberg.org/xchacha20-poly1305/husi/releases)
(虎兕) ～自建党/单节点梭哈 基于sing-box核心，稳定、简单易用、链式代理易操作 新协议、新特性都迅速跟进，纵向对比各平台 App/Core，都属协议覆盖率的前列 分流繁琐，但好在提供 Rule-set 匹配查询功能；UI走经典的Material Design公模风 >
- [Nekobox](https://github.com/MatsuriDayo/NekoBoxForAndroid)
～自建党/单节点梭哈 全协议支持、稳定、简单易用、链式代理易操作 分流繁琐；UI走经典的Material Design公模风 >
- [Karing](https://github.com/KaringX/karing/)
基于sing-box核心（并额外补充Vless-XHTTP），分流规则开箱即用、对新手最友好的sing-box GUI之一，全平台通用 覆写可选项少，最大缺点可能是UI一般！ >
- [V2rayNG](https://github.com/2dust/v2rayNG)
自建党/单节点梭哈 基于v2ray/xray核心，最早问世的代理工具之一，成熟稳定、简单易用 分流短板；UI走经典的Material Design公模风；👴🏻老同志App >
- [Surfboard](https://manual.getsurfboard.com/)
(冲浪板) ✂ 阉割主流协议 魔改v2ray核心的分流，UI 美观并对 Android 代理工具的审美情趣有极大贡献 协议残缺严重(如Vless-Reality/TUIC)，覆写可选项比FlClash少，核心本身已进入👴🏻老同志序列

#### 三类

>
- [YumeBox](https://github.com/YumeLira/YumeBox)
基于 mihomo 核心，UI 简洁美观；新版增加了预置的分流模板；集成 sub-store。另可选 smart 策略组 完成度很高的新项目 >
- [ShadowSocks-Android](https://github.com/shadowsocks/shadowsocks-android)
当代代理工具的开山鼻祖（2014.07） ✂✂✂ 阉割主流协议 ... 分流短板；UI走经典的Material Design公模风；👴🏻老同志App >
- [InsightBox](https://t.me/s/v2rayInsight)
(原v2rayInsight) 基于v2ray和sing-box核心的分流、简单易用、UI简洁美观 仿Surfboard的UI，v2ray核心本身已进入👴🏻老同志序列 >
- [Xray GUI](https://github.com/SaeedDev94/Xray/)
基于Xray核心，主流协议支持较全 分流短板 >
- [Clash Mi](https://github.com/KaringX/clashmi/)
基于Mihomo核心，全协议支持、分流，Mihomo核心的其他优点 KaringX的新开项目 >
- [FlClashX🆕](https://github.com/pluralplay/FlClashX)
基于成熟项目 FlClash 的🇷🇺俄罗斯fork，首页界面有小变化；比原版对 Android TV 的支持更佳 截至 v0.3.2 版，策略组内包括的节点较多（如400个）时，滑动易掉帧 >
- [Bettbox🆕](https://github.com/appshubcc/Bettbox)
基于成熟项目 FlClash 的 fork，首页界面有小变化；新增一些内核配置的选项 新项目 >
- [MikuBox for Android](https://github.com/HatsuneMikuUwU/MikuBoxForAndroid/)
基于sing-box核心，全协议支持、分流，其他参考Nekobox 从 Nekobox fork 的新项目，其他参考Nekobox；自 v1.4.3 起进入 EOL 状态 >
- [KunBox🆕](https://github.com/roseforljh/KunBox)
基于 sing-box 核心，UI 些许类似 Karing 新项目 >
- [Nekobox [by starifly]](https://github.com/starifly/NekoBoxForAndroid)
在Nekobox基础上，增加了新协议，以及分片设置等参数 从 Nekobox fork 的新项目，其他参考Nekobox >
- [Happ Proxy](https://github.com/Happ-proxy/happ-android)
自建党/单节点梭哈 Xray核心，主流协议支持较全，免费 分流短板 >
- [clash-xiaoy](https://github.com/aimy1/clash-xiaoy)
基于 mihomo 核心，针对 Clash Nyanpasu 的 UI 修改 fork 新项目 >
- [MonadBox 🆕](https://github.com/MonadBoxLab/MonadBox)
基于 mihomo 核心；YumeBox 的 fork 完成度很高的新项目 >
- [OneXray 🆕](https://github.com/OneXray/OneXray)
覆盖五大平台的 Xray 客户端 新项目；UI 略简陋 >
- [MConnect 🆕](https://t.me/mconnectofficial)
基于 V2Ray 核心；多端发布 小众项目 >
- [Vproxy](https://github.com/5vnetwork/vproxy/)
自建党/单节点梭哈 基于Xray核心，颇有想法的三位一体（VPS 节点搭建探针代理客户端），界面美观 较新的项目；分流短板（至少目前如此），导致仅匹配“自建党”的需求 >
- [Hiddify](https://github.com/hiddify/hiddify-next/)
🟡美以伊战争前夕，诈尸更新一次 魔改sing-box核心，简单易用，波斯风味app 虽基于singbox但分流短板；因断更已久，anyTLS等新协议支持不足 >
- [FlyClash](https://github.com/GtxFury/FlyClash/)
Mihomo类的另一GUI客户端，界面美观 较新的项目；仍在测试，apk安装包待发布；代码质量遭非议 >
- [Sudodroid](https://github.com/SUDOKU-ASCII/sudoku-android)
新代理协议
- [Sudoku (ASCII)](https://github.com/SUDOKU-ASCII/sudoku)
的官方客户端 较新的项目；只支持自家协议

#### 另类（依赖Root）

>
- [Box for Root](https://github.com/taamarin/box_for_magisk)
(BFR) 一站式包揽mihomo/Clash、sing-box、v2ray、xray等全明星阵容核心库，支持redir/TProxy/TUN等多模式 依赖 Magisk Manager、KernelSU Manager 或 APatch 安装 >
- [Surfing](https://github.com/GitMetaio/Surfing)
一从成熟项目 Box4Magisk 分支而来，基于mihomo/Clash核心，支持redir/TProxy/TUN等多模式 相对其他框架类工具的优势是，集成了开箱即用的配置文件 依赖 Magisk Manager、KernelSU Manager 或 APatch 安装 >
- [Box4Magisk](https://github.com/CHIZI-0618/box4magisk)
一站式包揽mihomo/Clash、sing-box、v2ray、xray等全明星阵容核心库，支持redir/TProxy/TUN等多模式 依赖 Magisk Manager、KernelSU Manager 或 APatch 安装 >
- [Box for Android](https://github.com/boxproxy/box/)
从成熟项目 Box for Root (BFR) 分支而来，一站式包揽mihomo/Clash、sing-box、v2ray、xray等全明星阵容核心库 较新的项目 >
- [akashaProxy](https://github.com/akashaProxy/akashaProxy)
基于mihomo，支持 TProxy/TUN 模式 依赖 Magisk Manager 或 KernelSU Manager >
- [Clash MIX](https://github.com/AXEVO/Clash-MIX)
基于mihomo，支持TUN模式 依赖 Magisk Manager 或 KernelSU Manager

#### 其他

>
- [V2ray/V2fly [裸核]](https://github.com/v2ray/v2ray-core/releases?page=25)
✂ 阉割主流协议 当代代理工具的里程碑（2015.09） 成熟稳定、消耗少 分流很折腾，需要手写定义outbound；跑裸核过于原教旨主义；虽有[V2fly团队](https://github.com/v2fly/v2ray-core/releases)
后继，但协议等跟进缓慢，👴🏻老同志 >
- [Xray [裸核]](https://github.com/XTLS/Xray-core/releases)
V2ray的演进（2020.11） 协议高大全、性能强 基于该核心的App/插件相对较少，跑裸核过于原教旨主义 >
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 协议高大全、易用性高 跑裸核过于原教旨主义 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心（2022.08） 协议高大全、性能强；极致体验党的福音，哪怕real-ip、哪怕不采用auto_redirect，它仍属迄今"最快国内体感最快国外体感"的唯二方案（另一是爱快/RouterOS虚拟网卡"伪多拨回环"分流方案，体感更极致但也更难部署） 部署对新手不友好；新兴核心的迭代过于激进，尤其1.10.x版本前/后，导致config.json很难向下兼容；跑裸核过于原教旨主义 > 一些已不再活跃的Apps，不再赘述 🔴已断更 补充：由于全球最大广告公司Google在Android 7.0（2016年8月）后不再允许非官方证书进行中间人(MitM)攻击，其后的安卓系统都无缘像iOS同类型Apps使用MitM去广告等。

### 🍎 iOS（含iPadOS）【2026-04-17起分类不再捆绑 tvOS 支持度，也不建议这样用】

#### 一类

>
- [ShadowRocket](https://apps.apple.com/app/shadowrocket/id932747118)
(小火箭) 🇺🇸$2.99 ～自建党/单节点梭哈 极为齐全的代理协议。简单易用、定价低廉、更新积极、链式代理易操作。当之无愧的销量第一 跟进新协议、新特性的速度在 iOS 端相对较快；纵向对比各平台 App/Core，基本属协议覆盖率的前列 分流繁琐，但并非不支持 >
- [Loon](https://apps.apple.com/app/loon/id1373567447)
🇺🇸$7.99（2025涨价后） ～买MitM，送代理工具 分流、集成MitM＋substore；近期更新后，主流协议覆盖短板基本补齐；去广告等 MitM 生态最为活跃 较之竞品，或更易断流；🟠分流规则的优先序易踩坑：本地规则 > 插件隐含规则 > 订阅规则；少数协议残缺如TUIC，但在iOS平台已经很不错。 >
- [Quantumult X](https://apps.apple.com/app/quantumult-x/id1443988620)
(QX) 🇺🇸$9.99（2025涨价后） ✂ 阉割主流协议 分流、集成MitM＋substore、相对省电、集成简易抓包工具；“古早年代”是爆款；近期更新后，主流协议覆盖短板基本补齐 🟠部分协议残缺(如HY2/TUIC/WG)；👴🏻老同志App >
- [Stash](https://apps.apple.com/app/stash-rule-based-proxy/id1596063349)
🇺🇸$5.99（2025涨价后） ～买代理工具，送MitM 分流、较全的协议支持、集成Tailscale内网穿透及分流、集成MitM＋substore、定价相对公允，*基本*兼容Clash配置与Mihomo规则集 配置文件与Mihomo不能100%互通。🟠代码[被控大面积抄袭开源GPL项目](https://t.me/haitun_channel/1530)，即便如此，对新协议的跟进仍慢（如缺anyTLS）且芝麻大的小更新就涨价$2，～阉割版Mihomo

#### 二类

>
- [Egern](https://apps.apple.com/app/id1616105820)
代理和MitM免费，余下功能🇺🇸$5.99 分流、集成MitM；集成可编程小组件，如服务器探针、货币盯盘等示例玩法；规则集、模块均兼容Surge版；模块也兼容 Loon；Rust 语言编写 协议支持范围在2025-09后已大幅改善，用户群体虽少，但开发者乐于采纳用户建议 >
- [Karing](https://apps.apple.com/app/karing/id6472431552)
分流，singbox核心/全协议支持（并额外补充Vless-XHTTP），tvOS可用，免费，其他参考Android版 UI略简陋，较iOS端竞品缺MitM，其他参考Android版 >
- [Pharos Pro](https://apps.apple.com/app/pharos-pro/id1456610173)
(水滴) 🇺🇸$2.99 基于mihomo核心，能做到一个配置文件通杀《全平台》；集成残血MitM 用户群体相对少；App Store版的更新频率较为佛系 >
- [Surge](https://apps.apple.com/app/surge-5/id1442620678)
订阅制🇺🇸$49.99/年 曾是代理工具的里程碑（2015.10） ✂ 阉割主流协议 集成MitM、substore，垃圾节点的克星Smart策略组，集成简易抓包工具➕简易内网穿透Ponte(非通用)➕闭源Snell协议(非通用) 与 iOS/NE 契合度最佳、性能最强 定价高＋协议残缺严重(包括但不限于Vless全家桶)。较之竞品app，易内存泄露，尤其当连接数较多或重度使用Smart策略组时；👴🏻老同志App 代理工具界 Omakase: 主理人有自己的调性，客人们没有“点菜”的余地，若妄想点菜可能遭主理人或粉头反手教育 >
- [Sing-box VT (App Store 1.11.x版)](https://apps.apple.com/app/sing-box-vt/id6673731168)
全协议支持、分流、最强DNS处理、省电优化好、更新积极、免费，迭代激进/屎山代码风险小，基本能做到一个配置文件通杀《全平台》 对于 iOS，它还有一小点独到优势：哪怕不用其他 Apps 刚需的“偏方”，它代理的 TG 也不转圈圈 GUI极其简陋、学习曲线陡峭；配置难度高/覆写全靠手搓config.json；迭代激进/旧配置文件可能跨版本不兼容 因作者的开发者账号故障，iOS端 ≥1.12.x版本 仅在TestFlight发布

#### 三类

>
- [Clash Mi](https://apps.apple.com/app/clash-mi/id6744321968)
全协议支持、分流，免费，兼容Mihomo配置与规则集、能做到一个配置文件通杀《全平台》 KaringX的新开项目 >
- [Streisand](https://apps.apple.com/app/streisand/id6450534064)
自建党/单节点梭哈 Xray核心，主流协议支持较全，免费 分流短板 >
- [Anywhere🆕](https://apps.apple.com/app/anywhere-proxy/id6758235178)
开源自制的核心，较全协议的支持，[详见 GitHub 页面](https://github.com/NodePassProject/Anywhere)；免费 新开项目，缺 AnyTLS >
- [Connect Now🆕](https://apps.apple.com/app/connect-now/id6749354119)
基于mihomo核心，能做到一个配置文件通杀《全平台》；免费 新项目 >
- [Happ Proxy](https://apps.apple.com/app/happ-proxy-utility/id6504287215)
自建党/单节点梭哈 参考Android版 参考Android版 >
- [incy 🆕](https://apps.apple.com/app/incy/id6756943388)
俄罗斯人开发的 Xray 客户端，UI 走毛子风 新项目 >
- [OneXray 🆕](https://apps.apple.com/app/onexray/id6745748773)
覆盖五大平台的 Xray 客户端 新项目；UI 略简陋 >
- [Nextin 🆕](https://apps.apple.com/us/app/nextin/id6754002454)
基于 mihomo 的客户端 新项目；面向机场主的商业化盈利 >
- [Vproxy](https://apps.apple.com/app/vproxy/id6744701950)
自建党/单节点梭哈 基于Xray核心，颇有想法的三位一体（VPS 节点搭建探针代理客户端），界面美观 较新的项目；分流短板（预计v1.3.x版改善），现仅匹配“自建党”需求 >
- [Hiddify](https://apps.apple.com/app/hiddify-proxy-vpn/id6596777532)
🟡美以伊战争前夕，诈尸更新一次 较全协议支持，免费，其他优点参考Android版 分流短板；因断更已久，anyTLS等新协议支持不足

#### 另类（依赖巨魔）

>
- [Sing-box for Apple](https://github.com/Elziy/sing-box-for-apple)
分流、集成MitM，对Singbox VT的fork，基本能做到一个配置文件通杀《全平台》 依赖巨魔（刚需旧版iOS 15～16.6.1）；用户群体少；欢迎尝试过的朋友分享体验

#### 其他

>
- [Tunna](https://apps.apple.com/app/tunna/id6471652937)
🇺🇸$9.99（2025涨价后） Xray核心 分流短板，用户群体少；没有Surge的命，得了Surge的病 >
- [Loon Lite](https://apps.apple.com/app/loon-lite/id6444029612)
🇺🇸$0.99 Loon涨价后的套装赠品，"小而丑"的代理App 定位尴尬（～Karing/Hiddify的阉割重命名收费？）。Loon搭售"捆绑物"，与其说赠品倒不如说本就 (注定) 不卖座！不如尽早断更，节省精力

### 🧿 HarmonyOS NEXT

>
- [ClashBox](https://github.com/xiaobaigroup/ClashBox)
(原ClashNEXT) 基于安卓端成熟的 FlClash 项目二次开发；自v1.4.7起，上架鸿蒙海外App商店 安装方式：先处于翻墙环境（或利用卓易通运行 Android 版代理软件），然后切换海外App商店进行下载 >
- [MConnect](https://t.me/mconnectofficial)
基于 V2Ray 核心；多端发布 安装方式：见 TG 频道 >
- [ClashMeta](https://github.com/likuai2010/ClashMeta)
🔴已断更

### 🎮 SteamOS

>
- [ToMoon](https://github.com/YukiCoco/ToMoon)
基于 Mihomo 核心 ... >
- [DeckyClash](https://github.com/chenx-dust/DeckyClash)
基于 Mihomo 核心 ...

## 🖥 电脑端 Computers

### 🪟 Windows

#### 一类

>
- [FlClash](https://github.com/chen08209/FlClash)
异常勤快的更新频率、轻量化，对Meta写法的配置文件可视化适配极佳，Clash/Mihomo类的所有优点 覆写可选项勉强够用，UI风格过于"手机化" >
- [V2rayN](https://github.com/2dust/v2rayN/releases/latest)
自建党/单节点梭哈 全协议支持(通过切换V2fly/Xray/Sing-box/Mihomo核心＋各种协议插件)、稳定、简单易用 🟢新协议、新特性都迅速跟进，纵向对比各平台 App/Core，都属协议覆盖率的第一！ 分流短板、UI复古，👴🏻老同志App >
- [Sparkle](https://github.com/xishang0128/mihomo-party)
(原Mihomo Party的分支A) 开发者(汐殇)是Mihomo核心的开发成员之一，也曾是Mihomo Party v1.6.0(含)之前版本的开发成员；对Meta写法的配置文件可视化适配极佳 过于臃肿；较成熟项目的新fork；随缘更新

#### 二类

>
- [Clash Party](https://github.com/mihomo-party-org/clash-party)
(原Mihomo Party的分支B) 因与MetaCubeX/Mihomo的软件名纠纷，已切换[OpenClash作者的Mihomo分支](https://github.com/vernesong/OpenClash/releases/tag/mihomo)
内建substore、高度覆写性，集成轻量模式/内存占用少，Clash/Mihomo类的所有优点 🟠项目自v1.6.0(不含)后已易主，继任开发者是某机场的利益相关者 >
- [GUI.for.SingBox](https://github.com/GUI-for-Cores/GUI.for.SingBox)
易用化的Singbox、点鼠标即可生成配置文件，模块化的插件中心（可拓展SpeedTest、规则集、云盘签到、OpenList、Substore等40+种） 配置文件只能靠点鼠标生成、无法被手搓/微调的外部json覆盖，年轻插件待时间检验 >
- [GUI.for.Clash](https://github.com/GUI-for-Cores/GUI.for.Clash)
特色参考GUI.for.SingBox，其他优点参考Clash/Mihomo类 用户群体不太多 >
- [Husi](https://codeberg.org/xchacha20-poly1305/husi/releases)
(虎兕) 🆕 ～自建党/单节点梭哈 参考Android版 参考Android版 >
- [Bettbox](https://github.com/appshubcc/Bettbox)
基于成熟项目 FlClash 的 fork，首页界面有小变化；新增一些内核配置的选项 新项目 >
- [Karing](https://github.com/KaringX/karing/)
参考Android版 参考Android版 >
- [Netch](https://github.com/netchx/netch)
🔴已断更，但(除软路由端PW2外)暂无替代品 专精游戏级UDP代理 不适合日常网页、协议残缺(如SS2022/TUIC/Vless-Reality)，👴🏻老同志App

#### 三类

>
- [Clash Nyanpasu](https://github.com/libnyanpasu/clash-nyanpasu)
Clash/Mihomo类的所有优点 随缘更新 >
- [Clash Mi](https://github.com/KaringX/clashmi)
参考Android版 参考Android版 >
- [Pantheon](https://github.com/Zephyruso/Pantheon)
🔴项目已改为私有 基于sing-box核心，以Web封装的GUI客户端。其开发者为 zashboard 作者，封装面板同为zash 新插件，缺少覆写项，现～带 Web 控制面板/订阅管理的裸核；新项目 >
- [Stelliberty 🆕](https://github.com/Kindness-Kismet/Stelliberty)
Clash/Mihomo类的所有优点，基于 Rust 和 Flutter 构造 新项目 >
- [FlClashX🆕](https://github.com/pluralplay/FlClashX)
基于成熟项目 FlClash 的🇷🇺俄罗斯fork，首页界面有小变化 较新的项目 >
- [Carton 🆕](https://github.com/821869798/carton)
基于 sing-box 核心；今天已经少见的非 Web 类技术开发 新项目；类官方 SFW 布局，无额外功能补充 >
- [clash-xiaoy🆕](https://github.com/aimy1/clash-xiaoy)
基于 mihomo 核心，针对 Clash Nyanpasu 的 UI 修改 fork 新项目 >
- [Happ Proxy](https://github.com/Happ-proxy/happ-desktop)
自建党/单节点梭哈 参考Android版 参考Android版 >
- [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/)
(CVR) 爆款、高度覆写性，集成轻量模式/内存占用少，更新积极，Clash/Mihomo类的所有优点 UI一般；≥2.3.0版本bug渐多 >
- [Pandora Box](https://github.com/snakem982/Pandora-Box)
Clash/Mihomo类的所有优点 用户群体小 >
- [ClashTui](https://github.com/JohanChane/clashtui)
猎奇的终端界面(TUI)、Clash/Mihomo类的所有优点 不适合新手 >
- [Throne](https://github.com/throneproj/Throne)
自建党/单节点梭哈 对原Nekoray的fork 分流短板 >
- [Sing-Box Windows](https://github.com/xinggaoya/sing-box-windows/)
易用化的Singbox、可自定义配置文件运行 截至v1.7.2仍不完善，如： 设置里提示放置核心的路径有误，正确的应为%LOCALAPPDATA%\\sing-box-windows\\sing-box ; 策略组横向平铺，当策略组过多时调整/切换都很棘手 >
- [OneBox](https://github.com/OneOhCloud/OneBox)
基于singbox核心，UI简洁 较新的项目，UI简洁 >
- [FlowZ 🆕](https://github.com/dododook/FlowZ)
基于singbox核心，UI简洁；链式代理操作便捷 较新的项目，UI简洁 >
- [Nekobox for PC 🆕](https://github.com/qr243vbi/nekobox)
自建党/单节点梭哈 对原Nekoray的fork 分流短板 >
- [OneXray 🆕](https://github.com/OneXray/OneXray)
覆盖五大平台的 Xray 客户端 新项目；UI 略简陋 >
- [XrayUI 🆕](https://github.com/PhoenixNil/XrayUI-dev)
基于 Xray 核心/span> 新项目 >
- [Vproxy](https://github.com/5vnetwork/vproxy/)
自建党/单节点梭哈 基于Xray核心，颇有想法的三位一体（VPS 节点搭建探针代理客户端），界面美观 较新的项目；分流短板（预计v1.3.x版改善），现仅匹配“自建党”需求 >
- [FlyClash](https://github.com/GtxFury/FlyClash)
Mihomo类的另一GUI客户端，界面美观 较新的项目；代码质量遭非议 >
- [IRBox🆕](https://github.com/frank-vpl/IRBox)
sing-box 和 xray 双核心调用，一种新 UI；伊朗开发者 软件更新可能受到伊朗前景的影响 >
- [Hiddify](https://github.com/hiddify/hiddify-next)
🟡美以伊战争前夕，诈尸更新一次 参考Android版 参考Android版 >
- [Nekoray](https://github.com/MatsuriDayo/nekoray/releases/latest)
自建党/单节点梭哈 🔴已断更 UI优化的v2rayN，调用Singbox/v2ray核心，Nekobox桌面版 分流短板 >
- [Sudoku Desktop 🆕](https://github.com/SUDOKU-ASCII/sudoku-desktop)
新代理协议[Sudoku (ASCII)](https://github.com/SUDOKU-ASCII/sudoku)
的官方客户端 较新的项目；只支持自家协议

#### 其他

>
- [V2ray/V2fly [裸核]](https://github.com/v2ray/v2ray-core/releases?page=25)
✂ 阉割主流协议 当代代理工具的里程碑（2015.09） 参考Android版 过于原教旨主义，其他参考Android版，👴🏻老同志 >
- [Xray [裸核]](https://github.com/XTLS/Xray-core/releases)
V2ray的演进（2020.11） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心（2022.08） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Clash及Premium [裸核]](https://github.com/Dreamacro/clash)
当代代理工具的另一里程碑（2018.06） 🔴已删库，后由Clash.Meta/Mihomo继任 最早的开源策略分流工具 > Clash for Windows (cfw) 🔴已删库 最早的基于Clash核心的GUI客户端 > Clash Verge 🔴已删库，由Clash Verge Rev继任 >
- [ClashN](https://github.com/2dust/clashN)
🔴已断更 >
- [lvory](https://github.com/sxueck/lvory)
🔴已删库 Sing-box的另一GUI客户端：简单无覆写 窗口管理按钮过于macOS化，视觉割裂；较新的项目 > 一些已不再活跃的Apps，不再赘述 🔴已断更

### 🍏 macOS

#### 一类

>
- [FlClash](https://github.com/chen08209/FlClash)
支持在状态栏切换节点，对窗口管理低效的macOS较便捷；其他参考Win版 参考Win版 >
- [V2rayN](https://github.com/2dust/v2rayN/)
自建党/单节点梭哈 🟢新协议、新特性都迅速跟进，纵向对比各平台 App/Core，都属协议覆盖率的第一！ 其他参考Win 参考Win，👴🏻老同志App >
- [Sparkle](https://github.com/xishang0128/mihomo-party)
(原Mihomo Party的分支A) 支持在状态栏切换节点，对窗口管理低效的macOS较便捷；其他参考Win版 参考Win版 >
- [Singbox for Mac](https://sing-box.sagernet.org/zh/clients/apple/)
(sfm) 全协议支持、分流、最强DNS处理、衔接Tailscale内网穿透、更新积极、免费，迭代激进/屎山代码风险小，基本能做到一个配置文件通杀《全平台》 GUI极其简陋、学习曲线陡峭；配置难度高/覆写全靠手搓config.json；迭代激进/旧配置文件可能跨版本不兼容

#### 二类

>
- [Clash Party](https://github.com/pompurin404/mihomo-party/releases)
(原Mihomo Party的分支B) 因与MetaCubeX/Mihomo的软件名纠纷，已切换[OpenClash作者的Mihomo分支](https://github.com/vernesong/OpenClash/releases/tag/mihomo)
在macOS比在Win上更丝滑，其他优点参考Win版 🟠参考Win版 >
- [GUI.for.SingBox](https://github.com/GUI-for-Cores/GUI.for.SingBox)
易用化的Singbox、点鼠标即可生成配置文件，模块化的插件中心（可拓展SpeedTest、规则集、云盘签到、OpenList、Substore等40+种） ＞v1.8.9版因无签名，须借助xattr -cr /Applications/XXX.app或[macOS小助手](https://macwk.com.cn/soft/macos-assistant)绕签。其他缺点参考Win版 >
- [ClashMac 🆕](https://github.com/666OS/ClashMac)
基于 mihomo 核心，利用 SwiftUI 开发的闭源代理工具；美观，整合了一些观赏性的功能 新项目；逐渐变得臃肿 >
- [GUI.for.Clash](https://github.com/GUI-for-Cores/GUI.for.Clash)
参考Win版 参考GUI.for.SingBox的macOS版 >
- [ClashX Meta](https://github.com/MetaCubeX/ClashX.Meta/releases)
对原ClashX的fork，由MetaCubeX官方维护；极度轻量化 UI形如Meta XD面板打包而成，配色的审美近期稍微有一点点改善但不多 >
- [Loon for Mac](https://t.me/LoonNews)
TBD 界面美观。其 MitM 脚本、模块等功能在 iOS 端当属强项，可移植到 macOS 端使用 新项目，持续完善中。由于软件生态不同，在 iOS 端的强项在 macOS 端则变得不再重要，且都有丰富的上位替代。加之，协议覆盖不全，导致短板较短、长板又不长。 >
- [Husi](https://codeberg.org/xchacha20-poly1305/husi/releases)
(虎兕) 🆕 ～自建党/单节点梭哈 参考Android版 参考Android版

#### 三类

>
- [Clash Mi](https://github.com/KaringX/clashmi)
参考Android版 参考Android版 >
- [FlClashX🆕](https://github.com/pluralplay/FlClashX)
基于成熟项目 FlClash 的🇷🇺俄罗斯fork，首页界面有小变化 较新的项目 >
- [Bettbox🆕](https://github.com/appshubcc/Bettbox)
基于成熟项目 FlClash 的 fork，首页界面有小变化；新增一些内核配置的选项 新项目 >
- [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/)
(CVR) 参考Win版 与macOS状态栏的融合做得不如FlClash/Sparkle/Clash Party/Surge Mac/Stash Mac；其他参考Win版 >
- [Throne](https://github.com/throneproj/Throne)
自建党/单节点梭哈 对原Nekoray的fork 分流短板 >
- [Happ Proxy](https://github.com/Happ-proxy/happ-desktop)
自建党/单节点梭哈 参考Android版 参考Android版 >
- [FlowZ 🆕](https://github.com/dododook/FlowZ)
基于singbox核心，UI简洁；链式代理操作便捷 较新的项目，UI简洁 >
- [OneBox 🆕](https://github.com/OneOhCloud/OneBox)
基于singbox核心，UI简洁 较新的项目，UI简洁 >
- [ClashBar 🆕](https://github.com/Sitoi/ClashBar)
基于 mihomo 核心，利用 SwiftUI 开发的代理工具；简洁、美观 新项目；BUG 较多 >
- [Singboard for Mac🆕](https://github.com/okunvei/singboard_for_mac)
基于singbox核心，UI简洁；基于[Singboard](https://github.com/Yuu518/singboard)的 fork 较新的项目，UI简洁 >
- [OneXray 🆕](https://github.com/OneXray/OneXray)
覆盖五大平台的 Xray 客户端 新项目；UI 略简陋 >
- [Vproxy](https://apps.apple.com/us/app/vproxy/id6744701950)
自建党/单节点梭哈 基于Xray核心，参考 Win 版 参考 Win 版 >
- [IRBox🆕](https://github.com/frank-vpl/IRBox)
sing-box 和 xray 双核心调用，一种新 UI；伊朗开发者 软件更新可能受到伊朗前景的影响 >
- [Hiddify](https://github.com/hiddify/hiddify-next/)
🟡美以伊战争前夕，诈尸更新一次 免费，其他参考Android版 参考Android版

#### 另类（Mac软路由）

>
- [Surge Mac](https://nssurge.com/)
年付制🇺🇸$50一台｜🇺🇸$70三台｜🇺🇸$100五台 ✂ 阉割主流协议 契合甜点需求、惧怕 OpenWrt 的用户 一句话圈粉：一站式提供DHCP托管➕简易流量统计➕简易内网穿透Ponte(～青春版Tailscale/Zerotier)➕简易抓包(～青春版WireShark/Charles/ProxyMan)等附加功能，兼顾浅层的专业用途；是预算充裕的甜点需求用户，对 “轻·软路由” 尝鲜的不二之选；其他优点参考iOS版 据娱乐回环测试，其在[macOS NE “牢房内”](https://developer.apple.com/documentation/networkextension)的性能优于竞品（～20 Gbps on M3）。🟠但若与 UTM 套娃 OpenWrt 虚拟机后的通用代理核心进行比较，则是小巫见大巫（如 某通用核心 ～150 Gbps on M3） 一句话祛魅：协议残缺严重(包括但不限于Vless全家桶)且泥古；易内存泄露；受[macOS NE](https://developer.apple.com/documentation/networkextension)"拖累，性能远不如Linux/OpenWrt插件；无 real-ip 代理；卖点之一的Ponte，稳定性不高且缺乏Tailscale-DERP (或Zerotier-Moon)式的中继配置项；试图包揽软路由的个别功能，但浅尝辄止；👴🏻老同志App 代理工具界 Omakase: 主理人有自己的调性，客人们没有“点菜”的余地，若妄想点菜可能遭主理人或粉头反手教育 >
- [Stash Mac](https://stash.ws/macos/pricing/)
买断制🇬🇧£48.0六台｜年付制🇬🇧£12.0三台 形如花几十英镑买一套 Mihomo 皮肤 内网穿透既包括自身的StashLink，也包括强大的 Tailscale 通用方案（但暂不支持DERP） 普通且自信的定价，代理和交互体验均不如同类(兼容)核心的CVR、FlClash等App；又一个试图包揽软路由常用功能的App，但跨界才艺比Surge for Mac更为局限；🟠代码[被控大面积抄袭开源GPL项目](https://t.me/haitun_channel/1530)

#### 其他

>
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心（2022.08） 参考Android版 过于原教旨主义，其他参考Android版 > ClashX Pro 🔴已删库 > 一些已不再活跃的Apps，不再赘述 🔴已断更

#### 关于 Mac软路由 的补充：

1️⃣ 《另类》序列的apps是对代理性能、软路由功能等要求不高时的易用之选。其局限如，不支持 UPnP；难叠加 TCP打鸡血，不适合距机场入口＞25ms省市的"650兆及以上宽带"用户；尤其 macOS 网络性能严重拖后腿，导致在 🍏 Mac Mini (M4）上竟然跑不过400元档的 RK3582 (Rockchip) 芯片 🗄 OpenWrt 软路由。

2️⃣ 若对代理性能、客制化有更高要求（如万兆网卡版 Mac Mini 用户），还是建议用[OrbStack (个人免费/商用付费/性能最强)](https://orbstack.dev/)、[PD (付费/性能折中)](https://www.parallels.com/products/desktop/)或[UTM (免费/性能最弱)](https://mac.getutm.app)虚拟 OpenWrt 做旁路由——插件参考[OpenWrt 软路由](#openwrt)进行选择。

### 🐧 Linux

#### 一类

>
- [FlClash](https://github.com/chen08209/FlClash)
参考Win版 参考Win版 >
- [V2rayN](https://github.com/2dust/v2rayN/)
自建党/单节点梭哈 🟢新协议、新特性都迅速跟进，纵向对比各平台 App/Core，都属协议覆盖率的第一！ 其他参考Win 参考Win，👴🏻老同志App >
- [Sparkle](https://github.com/xishang0128/mihomo-party)
(原Mihomo Party的分支A) 参考Win版 参考Win版 >
- [Singbox for Linux](https://sing-box.sagernet.org/zh/installation/package-manager/#__tabbed_3_1)
全协议支持、分流、最强DNS处理、衔接Tailscale内网穿透、更新积极、免费，迭代激进/屎山代码风险小，基本能做到一个配置文件通杀《全平台》 GUI极其简陋、学习曲线陡峭；配置难度高/覆写全靠手搓config.json；迭代激进/旧配置文件可能跨版本不兼容

#### 二类

>
- [Clash Party](https://github.com/pompurin404/mihomo-party/releases)
(原Mihomo Party的分支B) 因与MetaCubeX/Mihomo的软件名纠纷，已切换[OpenClash作者的Mihomo](https://github.com/vernesong/OpenClash/releases/tag/mihomo)
参考Win版 🟠参考Win版 >
- [GUI.for.SingBox](https://github.com/GUI-for-Cores/GUI.for.SingBox)
易用化的Singbox、点鼠标即可生成配置文件，模块化的插件中心（可拓展SpeedTest、规则集、云盘签到、OpenList、Substore等40+种） 参考Win版 >
- [GUI.for.Clash](https://github.com/GUI-for-Cores/GUI.for.Clash)
参考Win版 参考Win版 >
- [Husi](https://codeberg.org/xchacha20-poly1305/husi/releases)
(虎兕) 🆕 ～自建党/单节点梭哈 参考 Android 参考 Android

#### 三类

>
- [Pantheon](https://github.com/Zephyruso/Pantheon)
🔴项目已改为私有 基于sing-box核心，以Web封装的GUI客户端。其开发者为 zashboard 作者，封装面板同为zash 参考 Win 版 >
- [Stelliberty 🆕](https://github.com/Kindness-Kismet/Stelliberty)
Clash/Mihomo类的所有优点，基于 Rust 和 Flutter 构造 新项目 >
- [FlClashX🆕](https://github.com/pluralplay/FlClashX)
基于成熟项目 FlClash 的🇷🇺俄罗斯fork，首页界面有小变化 较新的项目 >
- [Bettbox🆕](https://github.com/appshubcc/Bettbox)
基于成熟项目 FlClash 的 fork，首页界面有小变化；新增一些内核配置的选项 新项目 >
- [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/)
(CVR) 参考Win版 参考Win版 >
- [Carton 🆕](https://github.com/821869798/carton)
基于 sing-box 核心；今天已经少见的非 Web 类技术开发 新项目；其他参考 Win 版 >
- [Throne](https://github.com/throneproj/Throne)
自建党/单节点梭哈 对原Nekoray的fork 参考 Win 版 >
- [Happ Proxy](https://github.com/Happ-proxy/happ-desktop)
自建党/单节点梭哈 参考Android版 参考Android版 >
- [OneBox](https://github.com/OneOhCloud/OneBox)
基于singbox核心，UI简洁 较新的项目，UI简洁 >
- [Nekobox for PC 🆕](https://github.com/qr243vbi/nekobox)
自建党/单节点梭哈 对原Nekoray的fork 参考 Win 版 >
- [OneXray 🆕](https://github.com/OneXray/OneXray)
覆盖五大平台的 Xray 客户端 新项目；UI 略简陋 >
- [IRBox🆕](https://github.com/frank-vpl/IRBox)
sing-box 和 xray 双核心调用，一种新 UI；伊朗开发者 软件更新可能受到伊朗前景的影响 >
- [Vproxy](https://github.com/5vnetwork/vproxy)
自建党/单节点梭哈 基于Xray核心，参考 Win 版 参考 Win 版 >
- [Hiddify](https://github.com/hiddify/hiddify-next/releases/latest)
🟡美以伊战争前夕，诈尸更新一次 参考Android版 其他参考Android版

#### 另类（Linux软路由）

>
- [Dae](https://github.com/daeuniverse/dae)
(大鹅) 基于eBPF的透明代理工具（Linux独占），直连性能极高 GUI缺乏、学习曲线陡峭、配置难度高 >
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 利用nftables以auto_redirect TUN模式运行，部署简便、性能较强。其他参考Android版 参考Android版 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心（2022.08） 利用nftables以auto_redirect TUN模式运行，部署简便、性能极强。其他参考Android版 参考Android版

#### 其他

>
- [V2ray [裸核]](https://github.com/v2ray/v2ray-core/releases?page=25)
✂✂ 阉割主流协议 当代代理工具的里程碑（2015.09） 参考Android版 过于原教旨主义，其他参考Android版，👴🏻老同志 >
- [Xray [裸核]](https://github.com/XTLS/Xray-core/releases)
V2ray的演进（2020.11） 参考Android版 过于原教旨主义，其他参考Android版

### 😈 FreeBSD/Unix (不含macOS)

>
- [Singbox](https://sing-box.sagernet.org/zh/installation/package-manager/#__tabbed_3_5)
全协议支持、分流、最强DNS处理、衔接Tailscale内网穿透、更新积极、免费，迭代激进/屎山代码风险小，基本能做到一个配置文件通杀《全平台》 GUI极其简陋、学习曲线陡峭；配置难度高/覆写全靠手搓config.json；迭代激进/旧配置文件可能跨版本不兼容 >
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心 参考Android版 过于原教旨主义，其他参考Android版 >
- [Xray [裸核]](https://github.com/XTLS/Xray-core/releases)
V2ray的演进（2020.11） 参考Android版 过于原教旨主义，其他参考Android版

## 🛗 路由器 Routers

### 🛜 硬路由：华硕——须刷官改/梅林固件

#### 一类

>
- [MerlinClash2](https://t.me/merlinclashcat)
(MC2) MC的精简重构、Clash/Mihomo类的所有优点 与前版MerlinClash不可共存；放弃支持ax56v2/ax57及更早设备，新生插件待完善 >
- [FancySS](https://github.com/hq450/fancyss)
(科学上网) 自建党/单节点梭哈 基于V2ray/Xray核心，并额外整合Naïve、TUIC等代理协议，对 WiFi 5 (802.11ac) 及之前的旧机型友好、简单易用 分流短板、UI一般，👴🏻老同志App

#### 二类

>
- [MerlinClash Lite](https://t.me/Philosophichat)
更新积极，其他参考Clash/Mihomo类优点 与MerlinClash和MerlinClash2均不可共存 >
- [Merlin XrayUI](https://github.com/DanielLavrushin/asuswrt-merlin-xrayui)
自建党/单节点梭哈 基于Xray核心的代理插件，勤于更新 依赖Entware插件(@软件中心安装) >
- [MerlinClash](https://t.me/merlinclashcat)
(MC) 🔴已断更，由MC2继任 爆款、Clash/Mihomo类的所有优点 UI略臃肿、对AC之前老机型不友好

### 🛜 硬路由：小米——须解锁SSH

>
- [ShellCrash](https://github.com/juewuy/ShellCrash)
(原[ShellCrash](https://t.me/ShellCrash)) 爆款、Mihomo/Singbox/Singbox-P任选核心、性能强且稳定、配置弹性尚可 覆写设置较少，高度修改配置文件刚需SCP/SFTP；sing-box核心使用步骤繁琐，须分成两个子配置文件

### 🗄 OpenWrt 软路由: amd64 & aarch64 & mips

#### 一类

>
- [OpenClash](https://github.com/vernesong/OpenClash)
(OC) 产品受众～Surge for Mac：主要契合甜点需求 覆写设置极其丰富（虽运行起来根本无需太多操作），使用订阅转换后的启动速度较慢（但Meta yaml写法下的启动较快）；其Meta核心是作者自己对Mihomo的闭源fork，引入[类Surge的Smart策略组](https://github.com/vernesong/OpenClash/releases/tag/mihomo)等新特性；其他参考Clash/Mihomo类的优点 界面臃肿、新手易迷茫，CoreMark两万分以下的CPU慎用；由于容错机制过强，导致用户DIY的yaml易被插件自带的覆写项覆盖，加上LuCI界面的菜单层级和选项极其多（很难排查究竟是哪些☑️覆盖了yaml），因此不适合追求*高度自定义*的进阶用户 >
- [PassWall](https://github.com/Openwrt-Passwall/openwrt-passwall)
(PW) 自建党/单节点梭哈 核心任选Xray/Singbox等、配置弹性较大、支持负载均衡、支持搭建节点、链式代理易操作 分流实现繁琐，👴🏻老同志App >
- [Nikki](https://github.com/nikkinikki-org/OpenWrt-nikki)
(原[MihomoTProxy](https://github.com/morytyann/OpenWrt-mihomo)) OpenClash瘦身版，在Meta yaml写法下的启动迅速 依赖Firewall4/nftables >
- [PassWall2](https://github.com/Openwrt-Passwall/openwrt-passwall2)
(PW2) 核心任选Xray/Singbox等、🎮游戏级UDP代理表现、可单独为UDP分流，其他优点参考PW 分流操作虽较之PW有简化，但仍显繁琐 >
- [Momo](https://github.com/nikkinikki-org/OpenWrt-momo)
Nikki的singbox版 Nikki开发者新写的sing-box插件；核心可替换为支持机场订阅provider的[reF1nd分支](https://t.me/sing_box_reF1nd/610)，使用步骤可参考海豚测速频道的[推文](https://t.me/haitun_channel/1646)
新项目；对TCP/UDP模式暂不支持覆写，对模式和DNS的tag名称[约束了特定的命名](https://github.com/nikkinikki-org/OpenWrt-momo/wiki#%E6%8F%92%E4%BB%B6%E4%B8%8E%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

#### 多数插件可从Github下载.run一键式安装：

>
- [bcseputetto/Are-u-ok](https://github.com/bcseputetto/Are-u-ok)
@絆城 打包版 [x86 & ARM] 🟢持续更新: dae & daed, HomeProxy, Nikki, OpenClash, PW, PW2, SSR-Plus >
- [AUK9527/Are-u-ok](https://github.com/AUK9527/Are-u-ok)
@絆城 打包版 [x86 & ARM] 🟢恢复更新: PW, PW2, SSR-Plus, OpenClash, AdGuardHome, MosDNS, 网易云灰色歌曲解锁, KMS服务器

#### 二类

>
- [HomeProxy](https://github.com/immortalwrt/homeproxy)
调用Singbox核心，由immortalWrt官方维护 依赖Firewall4/nftables >
- [ShadowSocksR Plus+](https://github.com/fw876/helloworld)
(SSR+/SSR Plus/酸酸乳) 自建党/单节点梭哈 简单易用、支持搭建节点，WiFi 5 (802.11ac) 时代的旧款硬路由CPU也轻松运行 分流短板、覆写设置也不多，👴🏻老同志App >
- [Daed](https://github.com/daeuniverse/daed)
(大鹅op版LuCI) 优点参考Linux版 用户群体不太多 >
- [ShellCrash](https://github.com/juewuy/ShellCrash)
优点参考硬路由所述 对于openwrt而言缺Luci，相当于"半裸核"，其他参考硬路由所述 >
- [V2rayA-openwrt](https://github.com/v2rayA/v2raya-openwrt)
自建党/单节点梭哈 Xray/V2ray核心可切换，WiFi 5 (802.11ac) 时代的旧款硬路由CPU也轻松运行 进入👴🏻老同志序列的V2ray核心

#### 三类

>
- [NekoBox](https://github.com/Thaolga/openwrt-nekobox)
可调用Mihomo/Singbox核心、HomeProxy瘦如闪电版(～带简易统计面板的裸核) 依赖PHP-CGI；若调用singbox则刚需Firewall4/nftables，年轻插件待时间检验 >
- [FullCombo Shark](https://github.com/muink/openwrt-fchomo)
(原FCHomo) OpenClash瘦身版 依赖Firewall4/nftables，年轻插件待时间检验 >
- [Neko](https://github.com/nosignals/openwrt-neko)
可调用Mihomo/Singbox核心、HomeProxy瘦如闪电版(～带简易统计面板的裸核) 依赖Firewall4/nftablesPHP-CGI，年轻插件待时间检验；可能断更 >
- [Sing-box [裸核]](https://github.com/SagerNet/sing-box/releases)
正在发展的潜力股代理核心（2022.08） 若在Firewall4/nftables环境下开auto_redirect也不麻烦；其他参考Android版 参考Android版

#### 其他

>
- [Xray [裸核]](https://github.com/XTLS/Xray-core/releases)
V2ray的演进（2020.11） 参考Android版 过于原教旨主义，其他参考Android版 >
- [Mihomo [裸核]](https://github.com/MetaCubeX/mihomo/releases)
(原Clash.Meta) 社区最活跃的代理核心（2021.12） 参考Android版 过于原教旨主义，其他参考Android版 >
- [ByPass](https://github.com/tianiue/luci-app-bypass)
🔴已断更 >
- [HelloWorld](https://github.com/OpenWrt-Actions/luci-app-vssr)
🔴已断更，由SSR+继任 > 一些已不再活跃的插件，不再赘述 🔴已断更

## ⚙️ 周边产品 Accessories

### 📒 规则集 Ruleset

#### GeoIP/GeoSite等通用规则集

>
- [Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)
🔥老字号GEOIP和GEOSITE源 许多规则源的规则源 dat格式 >
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat/releases/tag/latest)
Mihomo/MetaCubeX维护的规则源 从 Loyalsoldier、CHIZI-0618 等上游合并 dat格式 >
- [苍狼山庄 运营商IP段](https://ispip.clang.cn/)
电信/联通/移动/广电/教育网/鹏博士/长城宽带/电信通➕港澳台 从 IPNetDB、APNIC 等上游合并，支持IPv4和IPv6 txt/html等文本格式 >
- [CHIZI-0618/v2ray-rules-dat](https://github.com/CHIZI-0618/v2ray-rules-dat)
🔴已断更 从 Loyalsoldier 等上游合并 dat格式

#### Surge/Loon/QX/Shadowrocket等规则集

>
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule)
🔥知名的第三方规则集 从 Loyalsoldier 等上游合并 适配 各种Apps 的文本格式 >
- [Loon 模块库](https://hub.kelee.one/)
🍎 iOS覆写规则/模块 可莉的 Loon 模块 >
- [Surge 模块库](https://surge.qingr.moe)
🍎 iOS覆写规则/模块 基于可莉 Loon 模块的转译版 原生仅适配 Surge，其他App需借助[Script Hub](https://scripthub.vercel.app)进行转换方可使用 >
- [松果库 (Egern 模块库) 🆕](https://nutrepo.com/)
🍎 iOS覆写规则/模块 Egern 开发者 ([鼠爸](https://t.me/egern_daddy))建站的模块库 原生适配 Egern, Surge, Loon, QX, Stash >
- [whatshub](https://whatshub.top)
🍎 iOS覆写规则/模块

#### Mihomo/Stash/Clash规则集

>
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat/tree/meta/geo)
🧑‍💼MetaCubeX官方维护 从 Loyalsoldier、CHIZI-0618 等上游合并 list (classical文本)、yaml (文本)、mrs (二进制)、dat、db、mmdb 等格式 >
- [DustinWin/ruleset_geodata](https://github.com/DustinWin/ruleset_geodata/releases/tag/mihomo-ruleset)
从 Loyalsoldier 等上游合并，大多为融合规则集 list (classical文本)、yaml (文本)、mrs (二进制) 格式 >
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash)
🔥知名的第三方规则集 从 blackmatrix7、Loyalsoldier 等开源上游合并 list (classical文本)、yaml (文本)、mrs 格式 >
- [deezertidal/Stash](https://github.com/deezertidal/stash-override)
🍎 iOS覆写规则/模块 Stash专用

#### 注意: 在核心加载时的资源消耗上，二进制＜文本，建议优先采用 mrs 规则。Stash 3.1.1 (2025年6月)及之后的版本才支持 mrs 规则。

#### Singbox规则集

>
- [SagerNet/sing_geosite](https://github.com/SagerNet/sing-geosite/tree/rule-set)
🧑‍💼SagerNet官方维护: 域名 规则集 ... 适配version 3的 srs (二进制)、db 格式 >
- [SagerNet/sing_geoip](https://github.com/SagerNet/sing-geoip/tree/rule-set)
🧑‍💼SagerNet官方维护: IP 规则集 ... 适配version 3的 srs (二进制)、db 格式 >
- [MetaCubeX/meta-rules-dat/sing](https://github.com/MetaCubeX/meta-rules-dat/tree/sing)
隔壁MetaCubeX维护的sing-box规则集 从 Loyalsoldier、CHIZI-0618 等上游合并 适配version 2的 srs (二进制)、json (文本) 格式 >
- [DustinWin/ruleset_geodata](https://github.com/DustinWin/ruleset_geodata)
从 Loyalsoldier 等上游合并，大多为融合规则集 适配version 2～3的 srs (二进制)、json (文本) 格式
- [Senshinya/singbox_ruleset](https://github.com/senshinya/singbox_ruleset)
基于 blackmatrix7 的转译版 适配version 2的 srs (二进制)、json (文本) 格式

#### 注意: sing-box的version号存在两次迭代，现为 version 3，仅适配v1.11.x及以上的sing-box核心。

#### ⛔️ 防广告规则集（通用）

>
- [privacy-protection-tools/anti-AD](https://github.com/privacy-protection-tools/anti-AD)
(anti-AD) 🔥知名、广覆盖的防广告规则源 适配ADGuard, DNSMasq, SmartDNS, Easylist, Pi-Hole, Mihomo (mrs, yaml), Clash/Stash (yaml), QX, Sing-box (srs), Surge >
- [217heidai/adblockfilters](https://github.com/217heidai/adblockfilters)
(黑带) 🔥知名、较广覆盖的防广告规则源 较之其他，不支持MosDNS >
- [TG-Twilight/AWAvenue-Ads-Rule](https://github.com/TG-Twilight/AWAvenue-Ads-Rule)
或[网站版](https://doc.awads.cc/Sub.html)
(秋风) 🔥知名的防广告规则源 较之其他，不支持SmartDNS；Sing-box仅有json，Mihomo/Clash仅有yaml >
- [Cats-Team/AdRules](https://github.com/Cats-Team/AdRules)
或[网站版](https://adrules.top/)
适配ADGuard, SmartDNS, MosDNS, Clash, Sing-box, QX, Surge, Loon

#### 注意: 规则集对现今网页的广告防护有限。规则集＜MitM＜浏览器插件如 uBlock Origin

### 🧰 小工具 Toolkit

>
- [Sub-Store](https://github.com/sub-store-org/Sub-Store)
搭建私人订阅库，并实现订阅相关的一些处理 部署环境: Node.js 或 Docker (xream/sub-store:latest) >
- [Sublink Worker🆕](https://github.com/7Sageer/sublink-worker)
Clash/Mihomo/Sing-box/Surge相关的配置文件生成 部署环境: Node.js 或 Vercel 或 Docker (ghcr.io/7sageer/sublink-worker:latest) >
- [ConfigFlow🆕](https://github.com/thsrite/configflow)
Mihomo/Surge/MosDNS相关的配置文件生成 部署环境: Node.js 或 Vercel 或 Docker (thsrite/configflow:latest)，且在节点识别上依赖 Sub-Store >
- [Script Hub](https://github.com/Script-Hub-Org/Script-Hub)
关联: 🍎iOS覆写规则/模块 QX、Surge、Loon、Stash之间的模块/覆写转换 部署环境: Node.js 或 Docker (xream/script-hub:latest) >
- [SubCase](https://github.com/sion-codin/SubCase)
关联: 🤖Sub-Store 安卓 APK 封装的 sub-store，无需 Root 即可使用

### 🔁 订阅转换 SubConverter

>
- [https://sub.dler.io](https://sub.dler.io)
(墙洞官方/OpenClash推荐) >
- [https://nexconvert.com](https://nexconvert.com)
(奶昔官方, 支持Singbox) >
- [https://sub-web.wcc.best](https://sub-web.wcc.best)
(花云/YTOO/OpenClash推荐, 支持Singbox) >
- [https://sublink.dev](https://sublink.dev)
(库洛米/YTOO/花云推荐) >
- [https://amyconvert.com](https://amyconvert.com)
(Amy官方) >
- [https://sub.v1.mk](https://sub.v1.mk)
(支持Singbox, 支持Vless/HY2) >
- [https://subboost.org 🆕](https://subboost.org/)
(由 Linux.do [@RyanVan](https://linux.do/t/topic/1398113)开发的可视化 Clash/Mihomo 配置文件) >
- [https://sub.haitunt.org](https://sub.haitunt.org)
(本网站提供，支持Singbox, 支持Vless/HY2) >
- [https://scripthub.vercel.app](https://scripthub.vercel.app)
(QX、Surge、Loon、Stash之间的模块/覆写转换) 关联: 🍎iOS覆写规则/模块

## Acknowledgments

Original content by [Haitun](https://www.haitunt.org/).

This repository is just an archival mirror of the content.

## License

Original content is copyrighted by the original author. Code in this repository (if any) is MIT.