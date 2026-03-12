# ApiScanPlus
Burpsuite插件用于接口路径渗透测试


# ApiScanPlus

ApiScanPlus为Burpsuite打造的路由抓取与渗透工具插件，结合了(JsRouteScan+ChkApi+Linkfinder)等优秀项目。


参考项目![](https://github.com/0x727/ChkApi_0x727)

## 适用场景

- **API 未授权与越权测试**：发现可能存在未授权访问的 API 端点，或自定义参数一键测越权。

- **API 资产收集**：快速收集目标网站的所有 API

- **安全测试**：作为渗透测试的信息收集阶段工具

- **开发调试**：帮助开发者了解前端调用了哪些 API

  



**Display界面功能介绍**

- UrlPath：支持路由的勾选与过滤，列出所有Api的数量与路径协助分类扫描。
- Custom Headers：支持自定义包头参数，自动抓取当前网站的Head头为默认值。
- Blocked Scan Paths:支持白名单Routes添加，加入白名单后将不再对此路径进行发包扫描。
- Scan Root Path：支持自定义主动扫描的根目录如（/api、 /system）。
- Recursion Scan按钮：支持递归扫描，会获取UrlPath中的所有路由递归对当前网站的每一层路径进行扫描。

![image-20260312160027688](https://picui.ogmua.cn/s1/2026/03/12/69b27bc5c891d.webp)

显示勾选的路由数量，并以颜色区分

![image-20260312161310018](https://picui.ogmua.cn/s1/2026/03/12/69b27c20e49a1.webp)

**Config界面功能介绍**

- Passive Scan：支持被动探测，开启后所有匹配到的路由都会以Passive Scan Path中的值作为根目录来请求。
- Carry Headers：支持全局携带Header，开启后所有插件发起的请求均会携带此header。
- Request Method：请求的方式，包含GET与POST
- Thread Pools Number：线程池的线程数，默认为10
- Passive Scan Path：被动探测的根目录，默认为/
- GET Query Params:支持自定义GET请求中插入参数。
- POST Body Params：支持在POST请求中添加自定义参数。

![image-20260312160558492](https://picui.ogmua.cn/s1/2026/03/12/69b27c674a737.webp)

插入header参数与body参数

![image-20260312161818617](https://picui.ogmua.cn/s1/2026/03/12/69b27c6b02575.webp)



**ScanResult界面功能介绍**

- 支持状态筛选，双击状态码自动过滤，或者按钮过滤。
- 支持路由扫描次数统计（scanned-*），双击route自动过滤与排序。
- 支持目标勾选右键Scan again，方便一键特定目标重新扫描。
- 支持导出所有扫描结果或复制路由信息。

![image-20260312162226249](https://picui.ogmua.cn/s1/2026/03/12/69b27c94ae7f7.webp)

双击过滤路由，方便一键检索同一路由扫描差异。

![image-20260312162956111](https://picui.ogmua.cn/s1/2026/03/12/69b27c926d8b6.webp)
