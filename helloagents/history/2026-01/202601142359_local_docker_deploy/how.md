# 技术设计: 本地 Docker 部署（可直接启动）

## 技术方案
### 核心技术
- Docker 多阶段构建（Node 构建前端 + Python 运行后端）
- docker-compose 统一启动与数据卷挂载

### 实现要点
- 前端 Vite 配置 `outDir` 指向仓库根目录 `static/`，因此 Dockerfile 需要从构建阶段复制 `/static` 而非 `/frontend/dist`。
- 通过 `.dockerignore` 排除 `.env`、`data/`、`logs/` 等不应进入镜像的本地内容。
- 运行时端口由 `PORT` 环境变量控制，默认 `7860`；容器对外映射 `7860:7860`。

## 测试与部署
- **部署命令:** `docker compose up -d --build`
- **验证点:**
  - `docker compose ps` 显示容器 `Up`
  - `GET http://localhost:7860/` 返回 200（静态页面）
  - `GET http://localhost:7860/public/uptime` 返回 JSON

