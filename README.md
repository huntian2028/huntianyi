# 浑天仪 Huntianyi

> 浑天仪是中国古代观测天象的三维球仪。本项目借其名，以 three.js 在浏览器中重建一座"关系天球"：节点如星，关系如宿，旋转观测，万象尽收。

基于 three.js 的 3D 关系演示系统家族中的**空间 / 结构**视角：以西游记全景为样本，把节点按层级铺在天球环带上，旋转观测、总览全局。

> **状态**：规划 / 文档阶段，代码实现待启动；构建顺序 relation-core → 浑天仪 → 因陀罗网 → 推背图。

## 定位：空间 / 结构（看全局）

本系统独立功能：

- **天球环带布局**：按 天庭 / 人间 / 地府 / 西天 等层级分环带（仿赤道环 / 黄道环 / 子午环）。
- **轨道旋转 + 缩放 LOD + 环带聚焦**。
- **结构概览**：分类计数、密度热力、层级树。
- **全景快照导出**。

数据切面：`nodes` 的层级 / 分类 / 球面坐标。
明确不做：因果链深挖（归 [因陀罗网](https://github.com/huntian2028/indranet)）、时间推演与预测（归 [推背图](https://github.com/huntian2028/tuibeitu)）。

## 家族架构：薄核心 + 三独立应用

三套系统各占一个正交维度，共用一个薄核心，功能互不重叠：

| 系统 | 维度 | 定位 |
|---|---|---|
| **浑天仪 Huntianyi** | 空间 / 结构 | 看全局 |
| [因陀罗网 IndraNet](https://github.com/huntian2028/indranet) | 关系 / 因果 | 看联系 |
| [推背图 TuiBeitu](https://github.com/huntian2028/tuibeitu) | 时间 / 演进 | 看变化 |

- **relation-core（薄核心，独立包）**：只含渲染 bootstrap（scene / camera / controls / 渲染循环 / 拾取）、数据 schema 与校验、数据加载器；**不含任何业务布局与功能**。
- 依赖单向：app → core；app 之间不互相 import。
- 统一数据 schema：`nodes`（结构）/ `edges`（关系）/ `events`（时间序列），各 app 只消费自己的切面。

## 相关项目

- [因陀罗网 IndraNet](https://github.com/huntian2028/indranet) — 关系 / 因果
- [推背图 TuiBeitu](https://github.com/huntian2028/tuibeitu) — 时间 / 演进

## 许可证

本项目源码公开，采用 **PolyForm Noncommercial License 1.0.0**（SPDX：`PolyForm-Noncommercial-1.0.0`），许可证全文见仓库里的 [LICENSE](LICENSE) 文件。

> 一句话：**非商业用途免费用，商业用途要授权。**
>
> 注意：PolyForm Noncommercial 属于"源码可见"（source-available）许可证，**不是 OSI 认证的开源许可证**，它禁止商业使用。

### ✅ 可以免费做的

- 个人学习、研究、测试，自己在电脑上用，当桌面、当摆件都行。
- 修改代码、做二次创作，只要不用于商业用途。
- 学校、科研机构、公益组织、政府机构，以及公共安全/卫生、环境保护组织使用（不受经费来源限制）。
- 非商业地转发、分享，转发时请附上许可证（或许可证链接）和下面的版权声明。

### ❌ 未经授权不可以做的

- 公司或个体经营者在业务中使用，包括只在公司内部使用。
- 交付给客户、集成进付费产品或付费服务。
- 打包出售、二次售卖源码或安装包。
- 其他以营利为目的的使用。

如需商业授权，请联系版权持有人。

### 必须保留的版权声明

使用、修改或转发时，请保留 LICENSE 文件开头这一行：

```
Required Notice: Copyright (c) 2026 贤小二
```