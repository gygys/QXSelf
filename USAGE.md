# QuantumultX 自定义规则使用说明
# QuantumultX Custom Rules Usage Guide

## 目录 (Table of Contents)

1. [简介](#简介)
2. [文件结构](#文件结构)
3. [安装方法](#安装方法)
4. [分流规则说明](#分流规则说明)
5. [重写规则说明](#重写规则说明)
6. [自定义配置](#自定义配置)
7. [常见问题](#常见问题)

---

## 简介

本仓库提供了 QuantumultX 的自定义分流规则和重写规则，帮助用户更好地管理网络流量和屏蔽广告。

**主要功能：**
- 🚀 智能分流：自动区分国内外流量
- 🛡️ 广告拦截：屏蔽常见广告和追踪
- 📺 流媒体优化：针对主流流媒体平台的规则
- 🔄 URL重定向：自定义URL重写和重定向

---

## 文件结构

```
QXSelf/
├── Filter/              # 分流规则目录
│   ├── Custom.list      # 自定义分流规则
│   ├── AdBlock.list     # 广告拦截规则
│   └── Media.list       # 流媒体分流规则
├── Rewrite/             # 重写规则目录
│   ├── Custom.conf      # 自定义重写规则
│   ├── AdBlock.conf     # 广告拦截重写
│   └── Redirect.conf    # URL重定向规则
├── Conf/                # 配置文件目录
│   └── QuantumultX.conf # 完整配置模板
├── README.md            # 项目说明
└── USAGE.md             # 使用说明（本文件）
```

---

## 安装方法

### 方法一：使用完整配置文件

1. 下载 `Conf/QuantumultX.conf` 文件
2. 在 QuantumultX 中，点击右下角图标
3. 选择「配置文件」→「下载」
4. 输入配置文件的 URL 或选择本地文件
5. 重启 QuantumultX

**配置文件 URL：**
```
https://raw.githubusercontent.com/gygys/QXSelf/main/Conf/QuantumultX.conf
```

### 方法二：单独添加规则

#### 添加分流规则

1. 打开 QuantumultX 配置文件
2. 找到 `[filter_remote]` 部分
3. 添加以下内容：

```ini
# 自定义分流规则
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/Custom.list, tag=自定义规则, force-policy=全球加速, update-interval=86400, opt-parser=true, enabled=true

# 广告拦截规则
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/AdBlock.list, tag=广告拦截, force-policy=REJECT, update-interval=86400, opt-parser=true, enabled=true

# 流媒体规则
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/Media.list, tag=流媒体, force-policy=全球加速, update-interval=86400, opt-parser=true, enabled=true
```

#### 添加重写规则

1. 打开 QuantumultX 配置文件
2. 找到 `[rewrite_remote]` 部分
3. 添加以下内容：

```ini
# 自定义重写规则
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/Custom.conf, tag=自定义重写, update-interval=86400, opt-parser=false, enabled=true

# 广告拦截重写
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/AdBlock.conf, tag=去广告, update-interval=86400, opt-parser=false, enabled=true

# URL重定向
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/Redirect.conf, tag=重定向, update-interval=86400, opt-parser=false, enabled=true
```

---

## 分流规则说明

### Custom.list - 自定义分流规则

包含基础的分流规则，适用于日常使用：

- **直连规则 (DIRECT)**：国内网站和服务直接连接
  - 国内主流网站（百度、淘宝、京东等）
  - 局域网地址
  
- **代理规则 (PROXY)**：国际网站和服务通过代理
  - Google、YouTube、Facebook等
  - GitHub、Twitter等开发者工具
  
- **拒绝规则 (REJECT)**：广告和追踪域名

### AdBlock.list - 广告拦截规则

专门用于拦截广告的分流规则：

- 国际广告联盟（Google Ads、AdMob等）
- 国内广告联盟（百度广告、淘宝广告等）
- 移动应用广告
- 数据追踪服务

### Media.list - 流媒体规则

针对主流流媒体平台的分流规则：

- **国际流媒体**：Netflix、YouTube、Disney+、Spotify等
- **国内流媒体**：bilibili、爱奇艺、腾讯视频等

---

## 重写规则说明

### Custom.conf - 自定义重写规则

基础的重写规则模板，包括：

- URL重定向（HTTP到HTTPS）
- Header修改（User-Agent等）
- 响应体修改（需配合脚本）
- Cookie管理

### AdBlock.conf - 广告拦截重写

通过重写规则拦截广告：

- 拦截广告请求（reject-200）
- 拦截开屏广告（reject-img）
- 针对特定应用的广告拦截

### Redirect.conf - URL重定向

URL重定向和替换规则：

- HTTP到HTTPS自动跳转
- 搜索引擎重定向
- 移动站点到桌面站点重定向
- URL参数清理

---

## 自定义配置

### 修改分流策略

如果您想修改某个域名的分流策略，可以：

1. Fork 本仓库
2. 编辑对应的 `.list` 文件
3. 修改规则后面的策略（DIRECT、PROXY、REJECT）
4. 在 QuantumultX 中使用您的仓库链接

**示例：**
```ini
# 将 Google 改为直连
HOST-SUFFIX,google.com,DIRECT
```

### 添加自定义规则

在配置文件的 `[filter_local]` 或 `[rewrite_local]` 部分添加：

```ini
[filter_local]
# 添加自定义域名到代理列表
HOST-SUFFIX,example.com,PROXY

[rewrite_local]
# 添加自定义重写规则
^https?://example\.com/old https://example.com/new 302
```

### MITM 配置

使用重写规则需要启用 MITM（中间人攻击）：

1. 在 QuantumultX 中生成证书
2. 安装证书到系统
3. 在「设置」→「通用」→「关于」→「证书信任设置」中启用证书
4. 在配置文件的 `[mitm]` 部分添加需要解密的域名

---

## 常见问题

### Q1: 规则不生效怎么办？

**A:** 检查以下几点：
1. 确认规则已启用（enabled=true）
2. 确认策略组配置正确
3. 尝试手动更新规则
4. 检查 QuantumultX 日志

### Q2: 如何更新规则？

**A:** 
- 自动更新：规则会根据 `update-interval` 设置自动更新（默认86400秒=24小时）
- 手动更新：在 QuantumultX 配置页面，长按规则，选择「更新」

### Q3: MITM 不工作？

**A:** 确保：
1. 已生成并安装证书
2. 已在系统设置中信任证书
3. 在 `[mitm]` 部分添加了正确的域名
4. 关闭了其他可能冲突的网络工具

### Q4: 如何测试规则是否生效？

**A:** 
1. 在 QuantumultX 中查看「网络活动」
2. 访问相应的网站，观察连接策略
3. 查看日志中的匹配规则

### Q5: 可以同时使用多个规则文件吗？

**A:** 可以！QuantumultX 支持添加多个规则文件，规则按照从上到下的顺序匹配。

### Q6: 如何贡献规则？

**A:** 
1. Fork 本仓库
2. 创建新的分支
3. 添加或修改规则
4. 提交 Pull Request

---

## 免责声明

本项目仅供学习交流使用，请勿用于非法用途。使用本规则导致的任何问题，作者不承担任何责任。

## 许可证

MIT License

---

## 相关链接

- [QuantumultX 官方网站](https://quantumult.app/)
- [QuantumultX 官方文档](https://github.com/crossutility/Quantumult-X)
- [规则语法说明](https://github.com/crossutility/Quantumult-X/blob/master/README.md)

---

**最后更新：** 2025-11-15
