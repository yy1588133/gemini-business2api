# Changelog

本文件记录项目所有重要变更。
格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/),
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### 变更
- 增加 `.dockerignore`，缩小 Docker 构建上下文并避免将本地环境变量/运行数据打入镜像。
- 文档补充 `docker compose` 的启动方式，降低本地部署门槛。

### 修复
- 修复 Dockerfile 前端构建产物复制路径（前端 Vite `outDir` 指向 `../static`），使 `docker compose up --build` 可成功构建并启动。
- 修复管理面板「账号管理 → 账户配置（JSON）」在空配置时默认只读，导致无法输入新增账号的问题。
