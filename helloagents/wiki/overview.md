# Gemini Business2API

> 本文件包含项目级别的核心信息。详细的模块文档见 `modules/` 目录。

---

## 1. 项目概述

### 目标与背景
将 Gemini Business 能力转换为 OpenAI 兼容接口，对外提供 `/v1/chat/completions` 等端点，并提供内置管理面板用于账号与系统配置管理。

### 范围
- **范围内:** OpenAI 兼容对话接口、账号池与故障切换、内置管理面板、基础监控与公开状态页、Docker 本地部署
- **范围外:** 生产级高可用集群编排、自动化证书/域名接入、外部数据库依赖（当前以文件持久化为主）

---

## 2. 模块索引

| 模块名称 | 职责 | 状态 | 文档 |
|---------|------|------|------|
| backend | FastAPI 网关与业务逻辑 | ✅稳定 | [backend](modules/backend.md) |
| frontend | 管理面板前端（构建为静态资源） | ✅稳定 | [frontend](modules/frontend.md) |
| deployment | Docker / 本地部署与运行方式 | ✅稳定 | [deployment](modules/deployment.md) |

---

## 3. 快速链接
- [技术约定](../project.md)
- [架构设计](arch.md)
- [API 手册](api.md)
- [数据模型](data.md)
- [变更历史](../history/index.md)

