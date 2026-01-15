# API 手册

## 概述
本项目提供：
- OpenAI 兼容对话接口（核心：`/v1/chat/completions`）
- 内置管理面板与管理 API（用于账号/系统设置）
- 公开状态页与统计接口（无需认证）

## 认证方式
### 1) 管理面板认证
- `ADMIN_KEY` 为必需环境变量，用于登录管理面板。
- 登录流程由前端提交 `admin_key` 并由后端校验（详见 `frontend/` 与 `main.py`）。

### 2) OpenAI 兼容接口鉴权（可选）
当配置了 `API_KEY` 时，访问 `/v1/*` 需提供 `Authorization` 请求头：
- `Authorization: Bearer <API_KEY>` 或直接 `Authorization: <API_KEY>`

未配置 `API_KEY` 时会跳过鉴权（详见 `core/auth.py`）。

---

## 接口列表（精选）

### Public（无需认证）

#### GET /public/uptime
**描述:** 返回服务可用性/请求统计摘要（用于监控页展示）。

**查询参数:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| days | int | 否 | 1~90，默认 90 |

#### GET /public/stats
**描述:** 返回公开统计信息（访问量、请求量、近一分钟请求数等）。

#### GET /public/display
**描述:** 返回公开展示信息（Logo URL、对话入口 URL 等）。

#### GET /public/log
**描述:** 返回脱敏后的最近运行日志（用于公开日志页）。

---

### 管理面板

#### GET /
**描述:** 返回管理面板入口页（静态资源）。

#### GET /admin/health
**描述:** 管理端健康检查（需要已登录 Session）。

---

### OpenAI 兼容接口

#### POST /v1/chat/completions
**描述:** OpenAI Chat Completions 兼容接口（支持流式输出）。

**认证:** 见上文「OpenAI 兼容接口鉴权」。

