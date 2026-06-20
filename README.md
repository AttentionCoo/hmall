# 🚀 黑马商城 (HmMall) —— 高并发微服务电商解决方案

<div align="center">

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green?style=flat-square&logo=springboot)
![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-Alibaba-blue?style=flat-square&logo=spring)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange?style=flat-square&logo=mysql)
![Redis](https://img.shields.io/badge/Redis-7.x-red?style=flat-square&logo=redis)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-3.x-orange?style=flat-square&logo=rabbitmq)
![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)

<p align="center">
  <b>🔥 基于 Spring Boot 3.x 与 Spring Cloud Alibaba 深度构建的 B2C 分布式电商平台</b>
  <br />
  聚焦分布式数据一致性 · 高并发流量削峰 · 海量数据实时检索等电商核心痛点
</p>

</div>

---

## 📖 项目简介

`HmMall` 是一个生产级分布式电商解决方案。项目涵盖了从用户认证、全品类商品检索、购物车联动、高并发下单、分布式事务处理、可靠性支付到延时物流追踪的全生命周期业务，采用标准的微服务架构拆分，旨在提供一套高性能、高可用的技术落地模板。

---

## 🛠 核心技术栈 (Technology Stack)

| 维度 | 技术选型 | 落地场景与优势 |
| :--- | :--- | :--- |
| **微服务治理** | `Spring Boot 3.x` <br> `Spring Cloud Alibaba` | 深度利用 **AOT 编译优化**，提升容器启动速度与运行时效率。 |
| **注册/配置中心**| `Nacos` | 实现服务的动态发现、健康检查与配置集中式管理。 |
| **流量防护** | `Sentinel` | 提供全方位**流量控制、熔断降级与热点参数限流**，保障稳定性。 |
| **统一网关** | `Spring Cloud Gateway` | 负责动态路由转发、全局负载均衡、基于 **JWT** 的权限校验。 |
| **分布式事务** | `Seata (AT 模式)` | 优雅解决跨服务调用下的**数据最终一致性**问题。 |
| **高性能缓存** | `Redis` | 承载 Token 存储、商品热点数据、**秒杀库存预扣减**。 |
| **搜索引擎** | `Elasticsearch` | 构建千万级商品数据的**倒排索引**，实现多维度高亮、分词检索。 |
| **异步解耦** | `RabbitMQ` | 实现订单超时自动关闭、库存异步释放、物流状态异构通知。 |
| **链路与监控** | `SkyWalking` / `Docker` | 全链路追踪，秒级定位分布式环境下的性能瓶颈。 |

---

---

## ✨ 核心业务场景与技术落地

### 1. 分布式下单与数据最终一致性
> **解决方案：Seata AT 模式**
> 在“创建订单（`order-service`）”、“扣减库存（`item-service`）”、“核销优惠券（`user-service`）”三个微服务间开启全局事务，确保在网络抖动或服务异常时数据自动回滚，保障高并发下的资产安全。

### 2. 延迟取消机制与分布式可靠通知
> **解决方案：RabbitMQ 死信队列 (TTL + DLX)**
> 用户下单后向延时队列投递消息，30 分钟未支付则自动触发死信监听：系统自动取消订单、回滚商品库存，避免恶意占单占用服务器资源。

### 3. 数据异构与高性能搜索优化
> **解决方案：MQ 异步广播 + Elasticsearch**
> 当运营后台修改商品或上下架时，异步触发消息广播，`item-service` 监听并实时更新 Elasticsearch 索引，保证 C 端用户搜索的实时性，同时实现完美的读写分离。

---

## 🚀 快速启动 (Quick Start)

### 1. 克隆源码
```bash
git clone [https://github.com/AttentionCasria/hmall.git](https://github.com/AttentionCasria/hmall.git)
cd hmall

## 📦 模块拆分与架构设计 (Architecture)

项目采用**核心业务分层**与**接口解耦**的设计理念，严格规避微服务间的循环依赖。

# 一键编译并安装公共依赖

mvn clean install

---



### 🛠 主要优化点解析：

1. **视觉分层**：用 `<div align="center">` 把项目的 Logo、标题和 Badge 居中对齐，营造出大厂主流开源项目的规范感。

2. **结构表格化**：将“核心技术栈”从枯燥的纯文本列表升级为了**三列对比表格**，技术选型和落地场景一目了然，非常适合面试官快速抓取关键词。

3. **代码树点缀**：在模块拆分树状图中加入了富有表现力的 Emoji（如 👤, 🛍️, 🛒），比纯冷冰冰的英文字符更具可读性。

4. **自定义描述块**：使用 Markdown 的定义列表和引用语法（`>`）重新包装了核心业务场景和优化亮点，视觉上错落有致，重点突出。
