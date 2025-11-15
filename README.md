# QXSelf
QXDIY

## Academic-Direct.list
QuantumultX分流规则文件，用于直连学术出版商网站。

包含以下网站的直连规则：
- 爱思唯尔 (Elsevier) - elsevier.com, sciencedirect.com 等
- Cell出版社 - cell.com, cellpress.com 等
- 自然出版集团 (Nature) - nature.com, springer.com 等

### 使用方法
在 QuantumultX 配置文件的 `[filter_remote]` 部分添加：
```
https://raw.githubusercontent.com/gygys/QXSelf/main/Academic-Direct.list, tag=学术网站直连, force-policy=direct, enabled=true
```
