# 架构设计

## 总体架构
```mermaid
flowchart TD
    Client[OpenAI 兼容客户端/浏览器] --> API[FastAPI 网关 main.py]
    API --> Accounts[账号池/会话管理 core/*]
    API --> Data[(data/* 文件持久化)]
    API --> Static[静态资源 static/（管理面板）]
```

## 技术栈
- **后端:** Python 3.11 + FastAPI + Uvicorn
- **前端:** Vue 3 + Vite（构建为静态资源由后端托管）
- **存储:** 文件持久化（`data/settings.yaml`, `data/accounts.json` 等）
- **部署:** Dockerfile（前后端多阶段构建）+ docker-compose（端口映射与数据卷）

## 核心流程
```mermaid
sequenceDiagram
    participant C as Client
    participant A as FastAPI
    participant M as AccountManager
    participant G as Gemini Business

    C->>A: POST /v1/chat/completions
    A->>M: 选择账号/会话（可切换与重试）
    M->>G: 发起请求
    G-->>M: 返回结果
    M-->>A: 组装为 OpenAI 兼容响应
    A-->>C: JSON / SSE 流式响应
```

## 重大架构决策
完整的 ADR 存储在各变更的 how.md 中，本章节提供索引。

| adr_id | title | date | status | affected_modules | details |
|--------|-------|------|--------|------------------|---------|

