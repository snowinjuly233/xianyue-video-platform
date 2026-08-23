# 弦月视频平台

> 基于 Spring Cloud 与 Vue 3 的视频社区全栈学习实践项目

## 项目简介

这是一个围绕视频社区业务场景搭建的前后端分离微服务项目，主要用于记录我的 Java 全栈与微服务自学过程。

我希望通过这个项目把零散的知识点放进一套相对完整的业务中进行实践，包括用户认证、视频处理、实时通信、消息通知、全文检索、对象存储以及服务间调用等。项目目前以学习、调试和持续完善为主，不用于商业用途。

## 学习目标

- 理解 Spring Boot、Spring Cloud 微服务项目的拆分与协作方式
- 熟悉网关鉴权、服务发现、远程调用和公共模块复用
- 实践 MySQL、Redis、Elasticsearch、RocketMQ、MinIO 等组件
- 掌握 Vue 3 前端工程化、状态管理和接口联调流程
- 学习分片上传、断点续传、WebSocket 通信和视频转码等业务实现
- 通过实际项目训练问题定位、环境配置和系统集成能力

## 主要功能

- 视频上传、播放、点赞、评论、收藏和弹幕
- 视频分片上传与断点续传
- 用户注册、登录、个人资料及关注关系管理
- 图形验证码、手机号和邮箱登录注册
- 用户个人主页及主页内容展示
- 一对一实时私聊
- 关注动态、评论、点赞和私聊消息通知
- 视频与用户聚合搜索、关键词补全及高亮
- 文生文、文生图和智能 PPT 等 AI 功能
- 视频转码、压缩、截图等媒体处理能力

## 项目演示

https://github.com/user-attachments/assets/109a5b6e-c354-46ef-abf2-14ffede8b725

## 技术栈

| 分类 | 主要技术 |
| --- | --- |
| 前端 | Vue 3、Vue Router、Pinia、Element Plus、Axios、DPlayer、ECharts |
| 后端 | Java 8、Spring Boot 2.6.11、Spring Cloud、Spring Cloud Alibaba |
| 微服务 | Nacos、OpenFeign、Spring Cloud Gateway、LoadBalancer |
| 数据访问 | MySQL、MyBatis-Plus、MyBatis-Plus-Join、Druid |
| 缓存与搜索 | Redis、Elasticsearch |
| 消息与通信 | RocketMQ、WebSocket |
| 文件与媒体 | MinIO、阿里云 OSS、JAVE |
| 安全与接口 | Spring Security、JWT、Knife4j |
| 调度与链路 | XXL-JOB、Sleuth、Zipkin |
| AI 能力 | 讯飞星火 API |

## 项目结构

```text
.
├── java
│   ├── gateway       # API 网关、认证与路由
│   ├── user_center   # 用户、主页与关注关系
│   ├── video         # 视频、互动与媒体处理
│   ├── search        # 视频和用户搜索
│   ├── chat          # 实时私聊
│   ├── notice        # 动态与消息通知
│   └── common        # 公共实体、工具和基础能力
├── vue               # Vue 3 前端项目
└── sql.sql           # 数据库初始化脚本
```

## 本地运行

### 1. 准备环境

项目涉及的服务较多，请根据需要准备以下环境：

- JDK 8 与 Maven
- Node.js 与 npm、pnpm 或 yarn
- MySQL、Redis
- Nacos、RocketMQ
- Elasticsearch、MinIO

部分功能还依赖短信、邮件、对象存储和大模型等第三方服务。请使用自己的测试配置，并避免把密码、Token 或密钥提交到仓库。

### 2. 初始化数据库

创建本地数据库并导入根目录下的 `sql.sql`，然后修改各服务的本地配置。

### 3. 构建后端

```bash
cd java
mvn clean install
```

完成依赖服务和配置后，可通过 IDE 或 Maven 分别启动 `gateway`、`user_center`、`video`、`search`、`chat` 和 `notice` 模块。

### 4. 启动前端

```bash
cd vue
npm install
npm run serve
```

## 实践重点

- 将用户、视频、搜索、聊天和通知能力拆分为独立服务
- 使用 Gateway 与 JWT 处理统一入口和身份认证
- 使用 OpenFeign 完成服务间调用
- 使用 Redis 缓存高频数据与跨服务状态
- 使用 RocketMQ 解耦消息生产与消费流程
- 使用 Elasticsearch 实现聚合搜索、补全和高亮
- 使用 WebSocket 实现实时消息通信
- 使用 MinIO 与 JAVE 完成文件存储和视频处理
- 使用 Vue 3、Pinia 和 Axios 完成前端状态及接口管理
