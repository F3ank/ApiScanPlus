# ApiScanPlus

ApiScanPlus为Burpsuite打造的路由抓取与渗透工具插件，借鉴结合了(JsRouteScan+ChkApi+Linkfinder)等优秀项目，主要突出API抓的全、过滤更严谨方便、测试自由度更高等特点。

感谢项目：[JsRouteScan](https://github.com/F6JO/JsRouteScan)、[LinkFinder](https://github.com/GerbenJavado/LinkFinder)、[ChkApi](https://github.com/0x727/ChkApi_0x727)



## 适用场景

- **API 越权测试**：可自动抓取API或自行粘贴API到PATH，实现GET、POST、Header自定义参数，对目标进行鉴权测试。

- **资产收集**：快速收集目标网站的所有 API，以及深层路由下的JS与Path。

- **接口权限校验**：从历史流量中提取数据进行参数修改重放，实现一键越权测试。

--------------------------------------------------------------------------------------------------------------------------------
## 更新3.0
- 1.新增Auth模块，实现一键垂直&水平越权测试
- 2.完善VUE目标path提取，自动抓取渲染路径并进行route拼接
- 3.对历史流量拉取优化，防止过多route导致插件卡死状态

**auth模块介绍**：
首先使用burpsuite将目标所有功能点进行点击发包一次，然后导入至插件（每次拉取数据为最后一次访问并去重）
![image-20260313132424199](https://github.com/user-attachments/assets/97c03f9d-f03f-42f1-825b-706701ebbf5e)

选择填入需要进行的测试方式（垂直/水平）鉴权参数（自动替换包头值cookies:xxxxxx，如果为新增包头值则进行插入newcookies:xxxxxxxxx）
![image-20260313132424199](https://github.com/user-attachments/assets/5fe0e31a-5592-41b8-a18e-d5addbecb04f)

相似度为100%表示越权成功
![image-20260313132424199](https://github.com/user-attachments/assets/576794a7-2171-428c-b646-72ab32ee7a59)
越权失败
![image-20260313132424199](https://github.com/user-attachments/assets/c78c26ee-4654-4bb3-ac1e-2421649648bc)

--------------------------------------------------------------------------------------------------------------------------------
## 更新2.0
- 1.不再依赖被动探索，现在用户可在Http History界面右键选择"Send to ApiScanPlus"将自动获取目标至插件，避免由于浏览器缓存机制导致的PATH漏报。
- 2.完善内部过滤机制，Config新增自定义过滤机制功能，用户可根据正则自己完善规则。
- 3.新增Diff按钮可快速筛选同类响应包。
- 4.新增Pause Scan/Resume Scan按钮可暂停/恢复扫描。
- 5.结果状态为405的path将自动更改发包方式（GET/POST），重新发包一次。


---------------------------------------------------------------------------------------------------------------------------------


**Display界面功能介绍**

- UrlPath：支持路由的勾选与过滤，列出所有Api的数量与路径协助分类扫描。
- Custom Headers：支持自定义包头参数，自动抓取当前网站的Head头为默认值。
- Blocked Scan Paths:支持白名单Routes添加，加入白名单后将不再对此路径进行发包扫描。
- Scan Root Path：支持自定义主动扫描的根目录如（/api、 /system）。
- Recursion Scan按钮：支持递归扫描，会获取UrlPath中的所有路由递归对当前网站的每一层路径进行扫描。



工具界面展示：

![image-20260313132424199](https://github.com/user-attachments/assets/9fafdcbd-bb94-4c38-9646-802ba1d78555)

![image-20260313132803084](https://github.com/user-attachments/assets/ecb78c3e-4189-4d29-aff5-852340904ed3)

一键检索抓取的路径数量及名称
![image-20260312160027688](https://github.com/user-attachments/assets/58efa79a-057f-420b-acd9-6e17e09fff66)

可自由勾选需要扫描的路由，并以用进行颜色区分。

![image-20260312161310018](https://github.com/user-attachments/assets/2023c662-c8b0-458d-aa70-98397459ef30)

**Config界面功能介绍**

- Passive Scan：支持被动探测，开启后所有匹配到的路由都会以Passive Scan Path中的值作为根目录来请求。
- Carry Headers：支持全局携带Header，开启后所有插件发起的请求均会携带此header。
- Request Method：请求的方式，包含GET与POST
- Thread Pools Number：线程池的线程数，默认为10
- Passive Scan Path：被动探测的根目录，默认为/
- GET Query Params:支持自定义GET请求中插入参数。
- POST Body Params：支持在POST请求中添加自定义参数。


![image-20260313133023318](https://github.com/user-attachments/assets/20ee07e1-225a-4e7e-abc0-a5adb6379fd4)

插入header参数与body参数

![image-20260312161818617](https://github.com/user-attachments/assets/01cc1455-9806-4d9e-81c7-562b6c5524b2)

<img width="2364" height="723" alt="image-20260312161653004" src="https://github.com/user-attachments/assets/a492cef8-15fd-497a-9bb6-51dd9058ea20" />


**ScanResult界面功能介绍**

- 支持状态筛选，双击状态码自动过滤，顶部按钮也可进行过滤。
- 支持路由扫描次数统计（scanned-*），双击目标Route自动过滤与排序。
- 支持目标勾选右键Scan again，方便一键特定目标重新扫描。
- 支持扫描结果复制或文件导出（CVS）。

![image-20260312162226249](https://github.com/user-attachments/assets/b0068864-98e8-402b-8d48-9a8c1ef0a3e3)

双击选择的路由，方便一键检索同一路由不同批次的扫描差异。

![image-20260312162956111](https://github.com/user-attachments/assets/39527b9c-2058-4679-97fc-7e990b1ce7f7)
