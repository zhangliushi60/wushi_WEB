# 技术方案与架构设计

## 一、整体架构

前端: React 18 + TypeScript + Tailwind CSS + Tiptap 编辑器 + Zustand
后端: Node.js + Express + TypeScript + Prisma ORM
数据库: MySQL 8.0 + Redis 7

## 二、AI模型分层

| 任务 | 模型 | 成本/千次 |
|------|------|----------|
| 论文逐段批改 | DeepSeek V3 | 1元 |
| 复杂案例分析 | GPT-4o | 15元 |
| 论文语言润色 | Claude 3.5 | 10元 |
| 大纲生成 | DeepSeek V3 | 0.3元 |

## 三、核心API

- POST /api/papers/:id/review（SSE流式批改）
- POST /api/ai/suggest（AI论点推荐 SSE）
- POST /api/ai/outline（AI大纲生成 SSE）

## 四、部署

开发: Vite + Express 本地
生产: Vercel（前端）+ 腾讯云轻量服务器（后端）+ 腾讯云MySQL