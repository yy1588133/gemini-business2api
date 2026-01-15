# 数据模型

## 概述
本项目以文件持久化为主，默认存放在 `data/` 目录（容器内为 `/app/data`）。
推荐在 Docker 部署时将宿主机 `./data` 挂载到容器内，以避免重启后丢失配置。

---

## 数据文件

### data/settings.yaml
**描述:** 系统设置持久化文件（如 API_KEY、代理、图片生成配置、重试策略等）。

**来源与优先级:**
- 业务配置优先从 `data/settings.yaml` 读取，其次可由环境变量覆盖（详见 `core/config.py`）。
- 安全配置（如 `ADMIN_KEY`）仅来自环境变量，不写入 YAML。

### data/accounts.json
**描述:** 账号配置文件（多账号池）。

**说明:**
- 也可通过 `ACCOUNTS_CONFIG` 环境变量直接提供 JSON 数组字符串（优先级更高）。

