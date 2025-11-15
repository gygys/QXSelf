# QXSelf

QuantumultX 自定义分流、重写规则集合

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📖 简介

本仓库提供了 QuantumultX 的自定义分流规则（Filter Rules）和重写规则（Rewrite Rules），帮助用户更好地管理网络流量、屏蔽广告和优化网络体验。

## ✨ 特性

- 🚀 **智能分流**：自动区分国内外流量，优化访问速度
- 🛡️ **广告拦截**：屏蔽常见广告和追踪服务
- 📺 **流媒体优化**：针对 Netflix、YouTube、Disney+ 等主流平台
- 🔄 **URL重定向**：自定义 URL 重写和重定向规则
- 📝 **持续更新**：规则定期更新维护

## 📂 文件结构

```
QXSelf/
├── Filter/              # 分流规则
│   ├── Custom.list      # 自定义分流规则
│   ├── AdBlock.list     # 广告拦截规则
│   └── Media.list       # 流媒体规则
├── Rewrite/             # 重写规则
│   ├── Custom.conf      # 自定义重写
│   ├── AdBlock.conf     # 广告拦截重写
│   └── Redirect.conf    # URL重定向
├── Conf/                # 配置文件
│   └── QuantumultX.conf # 完整配置模板
└── USAGE.md             # 详细使用说明
```

## 🚀 快速开始

### 方法一：使用完整配置（推荐新手）

直接导入完整的配置文件：

```
https://raw.githubusercontent.com/gygys/QXSelf/main/Conf/QuantumultX.conf
```

### 方法二：单独添加规则

在 QuantumultX 配置文件中添加：

**分流规则 [filter_remote]：**
```ini
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/Custom.list, tag=自定义规则, force-policy=全球加速, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/AdBlock.list, tag=广告拦截, force-policy=REJECT, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/gygys/QXSelf/main/Filter/Media.list, tag=流媒体, force-policy=全球加速, update-interval=86400, opt-parser=true, enabled=true
```

**重写规则 [rewrite_remote]：**
```ini
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/Custom.conf, tag=自定义重写, update-interval=86400, opt-parser=false, enabled=true
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/AdBlock.conf, tag=去广告, update-interval=86400, opt-parser=false, enabled=true
https://raw.githubusercontent.com/gygys/QXSelf/main/Rewrite/Redirect.conf, tag=重定向, update-interval=86400, opt-parser=false, enabled=true
```

## 📚 详细文档

查看 [USAGE.md](./USAGE.md) 获取完整的使用说明，包括：

- 详细安装步骤
- 规则说明和配置
- 自定义方法
- 常见问题解答

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 来帮助改进规则！

## ⚠️ 免责声明

本项目仅供学习交流使用，请勿用于非法用途。使用本规则导致的任何问题，作者不承担任何责任。

## 📄 许可证

MIT License

## 🔗 相关链接

- [QuantumultX 官方网站](https://quantumult.app/)
- [QuantumultX 官方文档](https://github.com/crossutility/Quantumult-X)

---

**Star ⭐ 本项目以获取最新更新！**
