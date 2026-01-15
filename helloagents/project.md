# 项目技术约定

---

## 技术栈
- **后端:** Python 3.11 / FastAPI（见 `requirements.txt`）/ Uvicorn
- **前端:** Vue 3 + Vite（位于 `frontend/`；构建产物输出到仓库根目录 `static/`）
- **容器化:** Dockerfile（前后端多阶段构建）+ docker-compose

---

## 配置与环境变量
### 安全配置（仅环境变量）
- `ADMIN_KEY`：必需；管理面板登录使用
- `SESSION_SECRET_KEY`：可选；未设置时会自动生成随机值（每次启动可能变化）

### 业务配置（环境变量 > data/settings.yaml）
- `API_KEY`：可选；为 OpenAI 兼容端点增加鉴权（见 `core/auth.py`）
- `PROXY` / `BASE_URL`：可选；代理与基础地址

### 端口与跨域
- `PORT`：可选；默认 `7860`
- `FRONTEND_ORIGIN` / `ALLOW_ALL_ORIGINS`：可选；CORS 配置（见 `main.py`）

### 账号配置
- `ACCOUNTS_CONFIG`：可选；适用于容器化部署的 JSON 数组字符串（优先级高于文件）

---

## 数据持久化约定
- 默认数据目录为 `data/`（容器内为 `/app/data`）。
- 推荐通过 `docker-compose.yml` 将宿主机 `./data` 挂载到容器 `/app/data`，以持久化：
  - `data/settings.yaml`：系统设置
  - `data/accounts.json`：账号配置

---

## 日志与排障
- 默认输出到 stdout/stderr；容器环境使用 `docker compose logs -f` 查看。
- 关键启动失败点：未设置 `ADMIN_KEY` 会直接退出（见 `main.py`）。

