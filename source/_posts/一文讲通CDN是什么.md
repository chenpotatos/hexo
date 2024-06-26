---
title: 一文讲通CDN是什么
date: 2024-04-26 20:15:22
tags: front end
cover: https://tse1-mm.cn.bing.net/th/id/OIP-C.FzXG2jRBDHTGUZ3w4kL1bwAAAA?rs=1&pid=ImgDetMain
top_img: https://tse1-mm.cn.bing.net/th/id/OIP-C.FzXG2jRBDHTGUZ3w4kL1bwAAAA?rs=1&pid=ImgDetMain
---
> CDN的全称是Content Delivery Network，即内容分发网络。由于CDN是为加快网络访问速度而被优化的网络覆盖层，因此被形象地称为"网络加速器"。

CDN可以加快用户访问网络资源的速度和稳定性，减轻源服务器的访问压力。

## 一、CDN简介

**主要思路：** 尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节，使内容传输的更快、更稳定。

**实现方法：** 通过在网络各处放置 **节点服务器**所构成的在现有的互联网基础之上的一层 **智能虚拟网络**，CDN系统能够实时地根据网络流量和各节点的 **连接和负载**状况以及到用户的 **距离**和 **响应时间**等综合信息将用户的请求重新 **导向离用户最近的服务节点**上，加快访问速度。

**目的：** 使用户可 `&#x5C31;&#x8FD1;`取得所需内容，解决Internet网络拥挤的状况，提高用户访问网站的 `&#x54CD;&#x5E94;&#x901F;&#x5EA6;`。

**优势：**

1. CDN节点解决了跨运营商和跨地域访问的问题，访问延时大大降低；
2. 大部分请求在CDN边缘节点完成，CDN起到了分流作用，减轻了源站的负载。

## 二、CDN基本工作流程

首先是 **不使用CDN**的情况下的流程：

1. 用户在自己的浏览器中输入要访问的网站域名。
2. 浏览器向 本地DNS服务器 请求对该域名的解析。
3. 本地DNS服务器中如果缓存有这个域名的解析结果，则直接响应用户的解析请求。
4. 本地DNS服务器中如果没有关于这个域名的解析结果的缓存，则以递归方式向整个DNS系统请求解析，获得应答后将结果反馈给浏览器。
5. 浏览器得到域名解析结果，就是该域名相应的服务设备的 IP地址 。
6. 浏览器向服务器请求内容。
7. 服务器将用户请求内容传送给浏览器。

当 **使用了CDN**时，DNS 服务器根据用户 IP 地址，将域名解析成相应节点的缓存服务器IP地址，实现用户就近访问。使用 CDN 服务的网站，只需将其域名解析权交给 CDN 的全局负载均衡（GSLB）设备，将需要分发的内容注入 CDN，就可以实现内容加速了。

1. 当用户点击网站页面上的内容URL，经过 **本地**DNS系统解析，DNS 系统会最终将域名的解析权交给 `CNAME` 指向的 CDN 专用 DNS 服务器。
2. CDN 的 DNS 服务器将 CDN 的 **全局负载均衡设备** `IP` 地址返回用户。
3. 用户向 CDN 的全局负载均衡设备发起内容 URL 访问请求。
4. CDN 全局负载均衡设备根据用户 IP 地址，以及用户请求的内容URL，选择一台用户所属区域的区域负载均衡设备，告诉用户向这台设备发起请求。
5. 基于以下这些条件的综合分析之后，区域负载均衡设备会向全局负载均衡设备返回一台缓存服务器的IP地址：
  - 根据用户 IP 地址，判断哪一台服务器距用户最近；
  - 根据用户所请求的 URL 中携带的内容名称，判断哪一台服务器上有用户所需内容；
  - 查询各个服务器当前的负载情况，判断哪一台服务器尚有服务能力。
6. 全局负载均衡设备把服务器的 IP 地址返回给用户。
7. 用户向缓存服务器发起请求，缓存服务器响应用户请求，将用户所需内容传送到用户终端。如果这台缓存服务器上并没有用户想要的内容，而区域均衡设备依然将它分配给了用户，那么这台服务器就要向它的上一级缓存服务器请求内容，直至追溯到网站的源服务器将内容拉到本地。

## 三、CDN的作用

CDN最常用的功能当然是 `&#x52A0;&#x901F;`，但还有一些其他功能。

### 1. 加速访问

CDN可以使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。

还提供服务器端加速，解决由于用户访问量大造成的服务器过载问题；

### 2. 实现跨运营商、跨地域的全网覆盖

互联不互通、区域ISP地域局限、出口带宽受限制等种种因素都造成了网站的区域性无法访问。

CDN加速可以覆盖全球的线路，通过和运营商合作，部署IDC资源，在全国骨干节点商，合理部署CDN边缘分发存储节点，充分利用带宽资源，平衡源站流量。

### 3. 保障你的网站安全

CDN的负载均衡和分布式存储技术，可以加强网站的可靠性，相当无无形中给你的网站添加了一把保护伞，应对绝大部分的互联网攻击事件。防攻击系统也能避免网站遭到恶意攻击。

### 4. 异地备援

当某个服务器发生意外故障时，系统将会调用其他临近的健康服务器节点进行服务，进而提供接近100%的可靠性，这就让你的网站可以做到永不宕机。

### 5. 节约成本

能克服 **网站分布不均**的问题，投入使用CDN加速可以实现网站的全国铺设，你根据不用考虑购买服务器与后续的托管运维，服务器之间镜像同步，也不用为了管理维护技术人员而烦恼，并且能降低网站自身建设和维护成本。

### 6. 让你更专注业务本身

CDN加速厂商一般都会提供一站式服务，业务不仅限于CDN，还有配套的云存储、大数据服务、视频云服务等，而且一般会提供7x24运维监控支持，保证网络随时畅通，你可以放心使用。并且将更多的精力投入到发展自身的核心业务之上。

## 四、CDN工作原理

CDN的基本原理是广泛采用各种缓存服务器，将这些缓存服务器分布到用户访问相对集中的地区或网络中，在用户访问网站时，利用全局负载技术将用户的访问指向距离最近的工作正常的缓存服务器上，由缓存服务器直接响应用户请求。

### 1. 用户访问cdn资源的过程

1. 用户向浏览器输入www.web.com这个域名，浏览器第一次发现本地没有DNS缓存，则向网站的DNS服务器请求；
2. 网站的DNS域名解析器设置了CNAME，指向了www.web.51cdn.com,请求指向了CDN网络中的智能DNS负载均衡系统；
3. 智能DNS负载均衡系统解析域名，把对用户响应速度最快的IP节点（CDN服务器）返回给用户；
4. 用户向该IP节点（CDN服务器）发出请求；
5. 由于是第一次访问，CDN服务器会向原web站点请求，并缓存内容；
6. 请求结果发给用户。

### 2. cdn主要特点

1. **本地Cache加速** 提高了企业站点（尤其含有大量图片和静态页面站点）的访问速度，并大大提高以上性质站点的稳定性
2. **镜像服务** 消除了不同运营商之间互联的瓶颈造成的影响，实现了跨运营商的网络加速，保证不同网络中的用户都能得到良好的访问质量。
3. **远程加速** 远程访问用户根据DNS负载均衡技术智能自动选择Cache服务器，选择最快的Cache服务器，加快远程访问的速度
4. **带宽优化** 自动生成服务器的远程Mirror（镜像）cache服务器，远程用户访问时从cache服务器上读取数据，减少远程访问的带宽、分担网络流量、减轻原站点WEB服务器负载等功能。
5. **集群抗攻击** 广泛分布的CDN节点加上节点之间的智能冗余机制，可以有效地预防黑客入侵以及降低各种D.D.o.S攻击对网站的影响，同时保证较好的服务质量 。

## 五、CDN对网络的优化：

1. 解决服务器端的"第一公里"问题
2. 缓解甚至消除了不同运营商之间互联的瓶颈造成的影响
3. 减轻了各省的出口带宽压力
4. 缓解了骨干网的压力
5. 优化了网上热点内容的分布

**第一公里** 是指万维网流量向用户传送的第一个出口，是网站服务器接入互联网的链路所能提供的带宽。 这个带宽决定了一个 网站能为用户提供的访问速度和并发访问量。如果业务繁忙，用户的访问数越多，拥塞越严重，网站会在最需要向用户提供服务时失去用户。

**中间一公里** 代表互联网中节点与节点之间的传输网络。

**最后一公里** 万维网流量向用户传送的最后一段接入链路。

## 六、CDN的应用场景

### 1. 网站站点/应用加速

站点或者应用中大量静态资源的加速分发，建议将站点内容进行动静分离，动态文件可以结合云服务器ECS，静态资源如各类型图片、html、css、js文件等，建议结合 对象存储OSS 存储海量静态资源，可以有效加速内容加载速度，轻松搞定网站图片、短视频等内容分发

### 2. 视音频点播/大文件下载分发加速

支持各类文件的下载、分发，支持在线点播加速业务，如mp4、flv视频文件或者平均单个文件大小在20M以上，主要的业务场景是视音频点播、大文件下载（如安装包下载）等，建议搭配对象存储OSS使用，可提升回源速度，节约近2/3回源带宽成本。

### 3. 视频直播加速（内测中）

视频流媒体直播服务，支持媒资存储、切片转码、访问鉴权、内容分发加速一体化解决方案。结合弹性伸缩服务，及时调整服务器带宽，应对突发访问流量；结合媒体转码服务，享受高速稳定的并行转码，且任务规模无缝扩展。目前CDN直播加速已服务内部用户测试并优化，即将上线

### 4. 移动应用加速

移动APP更新文件（apk文件）分发，移动APP内图片、页面、短视频、UGC等内容的优化加速分发。提供httpDNS服务，避免DNS劫持并获得实时精确的DNS解析结果，有效缩短用户访问时间，提升用户体验。

## 七、CDN缓存

缓存是 `&#x7A7A;&#x95F4;&#x6362;&#x65F6;&#x95F4;`的思路，通过使用多余的空间，换来更快的访问速度。

* 不使用cdn缓存时

所有的用户都直接访问源服务器

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/97533f31385343498f3857eab1d01b3a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

* 使用cdn缓存时

客户端浏览器先检查是否有本地缓存是否过期，如果过期，则向CDN边缘节点发起请求，CDN边缘节点会检测用户请求数据的缓存是否过期，如果cdn数据没有过期，则直接响应用户请求，此时一个完成http请求结束；如果cdn数据已经过期，那么CDN还需要向源站发出回源请求，来拉取最新的数据。

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/526d6452f50147a98f0d29275c5fc78f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

**缓存优点：** CDN的分流作用不仅减少了用户的访问延时，也减少的源站的负载。

**缺点：** 当网站更新时，如果CDN节点上数据没有及时更新，即便用户再浏览器使用Ctrl+F5的方式使浏览器端的缓存失效，也会因为CDN边缘节点没有同步最新数据而导致用户访问异常。

### 八、解决CDN缓存更新的办法

1. 资源url参数加时间戳

url的参数加上时间戳，每次更新时时间戳也跟随更新，重新使cdn边缘节点同步源服务器最新数据。

```sh
http://www.cdn.com/static/images/test.png
http://www.cdn.com/static/images/test.png?_t=202012290910
```

1. 调用cdn服务商提供的 **刷新缓存**接口

CDN边缘节点对开发者是透明的，相比于浏览器Ctrl+F5的强制刷新来使浏览器本地缓存失效，开发者可以通过CDN服务商提供的"刷新缓存"接口来达到清理CDN边缘节点缓存的目的。

这样开发者在更新数据后，可以使用"刷新缓存"功能来强制CDN节点上的数据缓存过期，保证客户端在访问时，拉取到最新的数据。

## 七、cdn的组成

### 1. 部署架构

CDN 系统设计的首要目标是尽量 **减少用户的访问响应时间**，为达到这一目标，CDN 系统应该尽量将用户所需要的内容 **存放在距离用户最近的位置**。也就是说，负责为用户提供内容服务的 Cache 设备应部署在物理上的网络边缘位置，我们称这一层为 `CDN&#x8FB9;&#x7F18;&#x5C42;`。CDN 系统中负责全局性管理和控制的设备组成 `&#x4E2D;&#x5FC3;&#x5C42;`，中心层同时保存着最多的内容副本，当边缘层设备未命中时，会向中心层请求，如果在中心层仍未命中，则需要中心层向源站回源。

不同CDN系统设计之间存在差异，中心层可能具备用户服务能力，也可能不直接提供服务，只向下级节点提供内容。如果CDN网络规模较大，边缘层设备直接向中心层请求内容或服务会造成中心层设备压力过大，就要考虑在边缘层和中心层之间部署一个 `&#x533A;&#x57DF;&#x5C42;`，负责一个区域的管理和控制，也保存部分内容副本供边缘层访问。

如图是一个典型的CDN系统三级部署示意图:

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6db24ee3dcb84eed84b7736b09bdaec9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

### 2. 设备组成

CDN网络中包含的功能实体主要由以下几个部分组成：

* 内容缓存设备
* 内容交换机
* 内容路由器
* CDN内容管理系统

### 1. 内容缓存设备

内容缓存为 **CDN网络节**点，位于用户接入点，是面向最终用户的内容提供设备，可缓存静态Web内容和流媒体内容，实现内容的边缘传播和存储，以便用户的就近访问。

### 2. 内容交换机

内容交换机处于 **用户接入集中点**，可以均衡单点多个内容缓存设备的负载，并对内容进行缓存负载平衡及访问控制。

### 3. 内容路由器

内容路由器负责将用户的请求 **调度到适当的设备**上。

内容路由通常通过负载均衡系统来实现，动态均衡各个内容缓存站点的载荷分配，为用户的请求选择最佳的访问站点，同时提高网站的可用性。

内容路由器可根据多种因素制定路由，包括站点与用户的临近度、内容的可用性、网络负载、设备状况等。

**负载均衡系统是整个CDN的核心。负载均衡的准确性和效率直接决定了整个CDN的效率和性能。**

### 4. 内容管理系统

内容管理系统负责整个CDN的 **管理**，是 **可选部件**，作用是进行内容管理，如内容的注入和发布、内容的分发、内容的审核、内容的服务等。

