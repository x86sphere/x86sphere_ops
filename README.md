# X86sphereOps 自动化运维平台


**X86sphereOps 自动化运维平台** 是一款面向企业级 IT 基础设施的数字化、智能化运维管理系统。系统基于 **Golang (Gin)** 后端与 **Vue 3 (Vben Admin)** 前端架构构建，集成了自动化流水线、目录导航、文档中心、AD 域控集成及全方位的日志审计功能，旨在为运维团队提供统一、高效、安全的工作门户。

---

## 🚀 核心架构与技术栈

### 后端 (Backend)
- **核心框架**: [Golang 1.22+](https://go.dev/) + [Gin Web Framework](https://gin-gonic.com/)
- **数据库**: [PostgreSQL 18+](https://www.postgresql.org/) (关系型存储)
- **缓存/会话**: [Redis 8.2+](https://redis.io/) (JWT 黑名单、热点数据)
- **持久层**: [GORM](https://gorm.io/) (支持 AutoMigrate 自动建表与数据修复)
- **安全**: JWT (JSON Web Token) + AES-256 数据加密 + bcrypt 密码哈希

### 前端 (Frontend)
- **基础框架**: [Vue 3.4+](https://vuejs.org/) (Composition API)
- **工程化**: [Vite](https://vitejs.dev/) + [pnpm Monorepo](https://pnpm.io/)
- **UI 组件库**: [Naive UI](https://www.naiveui.com/)
- **管理模板**: [Vben Admin](https://github.com/vbenjs/vue-vben-admin)
- **状态管理**: [Pinia](https://pinia.vuejs.org/)

---

## 🛠️ 主要功能模块

### 1. 运维自动化 (Automation)
- **Jenkins 实例管理**: 支持多 Jenkins 实例接入、在线连接探测。
- **任务同步与发布**: 自动同步 Jenkins Jobs，支持参数化构建与实时日志查看。
- **构建历史**: 记录所有 Jenkins 发布流水线状态，实现故障追溯。

### 2. 系统管理 (System)
- **用户权限**: 基于 RBAC (基于角色的访问控制) 模型，支持多种角色权限配置。
- **AD 域集成**: 支持 Active Directory 用户同步与认证，适配混合环境办公。
- **部门/菜单**: 灵活配置组织架构及侧边栏动态路由。
- **中间件配置**: 集成 Jenkins 与 AD 的全局参数设置。

### 3. 内容与知识管理 (Cms)
- **文档中心**: 结构化存储运维文档、白皮书。
- **公告通知**: 发布全网或定向业务公告，支持强制弹窗与阅读状态追踪。
- **导航市场**: 内部业务系统一键直达，支持分类管理。

### 4. 日志审计中心 (Monitoring)
- **全链路追踪**: 包含登录日志、操作日志（CUD 操作自动记录）、权限变更日志及 API 回调日志。
- **健康探测**: 集成接口存活监测，适配容器云环境编排需求。

---

## 📦 快速部署 (Docker Compose)

系统已完成全栈容器化适配，推荐在 Linux 环境使用 Docker 一键部署：

```bash
# 1. 检查配置项
# 确认 x86sphere_ops_admin/config/config.yaml 中的数据库与 Redis 参数

# 2. 一键启动 (自动执行 DB -> Redis -> Backend -> Frontend 启动序列)
docker-compose up -d

普通用户登录/AD没有配置，配置好了就可以登录
- **账户**: admin
- **密码**: Admin123#

# 3. 验证
# 访问 http://服务器IP:80 (前端)
# 访问 http://服务器IP:8083/api/v1/healthz (后端状态)
```

---

## 🔒 生产规范与建议

1. **配置隔离**: 生产环境下，请将 `config.yaml` 中的 `server.mode` 设置为 `release`，并启用 JWT 的 Redis 校验。
2. **数据持久化**: 数据库数据默认保存在宿主机的 `./data/postgres`，请定期执行物理备份。
3. **日志滚动**: 生产环境默认保留 7 天日志，可通过 `config.yaml` 的 `max_age` 动态调整。

---

## 📄 版权信息
© 2026 **X86sphereOps 自动化运维平台**. 版权所有。

## 截图
<img width="1746" height="1275" alt="image" src="https://github.com/user-attachments/assets/cbdf2179-ebf8-4d1e-994e-8336d4fc56ba" />
<img width="1748" height="1275" alt="image" src="https://github.com/user-attachments/assets/ed3608a6-372f-4205-8088-b1197937fcd0" />
<img width="1746" height="1271" alt="image" src="https://github.com/user-attachments/assets/762214eb-baff-40d9-855b-e738c418f785" />
<img width="1750" height="1264" alt="image" src="https://github.com/user-attachments/assets/fd78078f-50cc-4fa8-a576-75ecf7324b45" />
<img width="1743" height="1277" alt="image" src="https://github.com/user-attachments/assets/53be096e-dbe5-4f5f-975a-847049bf8362" />
<img width="1742" height="1282" alt="image" src="https://github.com/user-attachments/assets/7a9b905b-fe24-464b-aca5-dfa79448dfdf" />
<img width="1740" height="1275" alt="image" src="https://github.com/user-attachments/assets/c0204906-f283-4745-ae17-2cd6c841a5d5" />
<img width="1752" height="1272" alt="image" src="https://github.com/user-attachments/assets/6718dba1-fa58-4130-b9c0-ee9e8f1f2310" />
<img width="1740" height="1272" alt="image" src="https://github.com/user-attachments/assets/b5e79ba1-383d-434d-a672-d9ec5a496a1e" />
<img width="1751" height="1279" alt="image" src="https://github.com/user-attachments/assets/9e3ea325-418f-459f-8d2a-6e6aa809d8cc" />
<img width="1750" height="1272" alt="image" src="https://github.com/user-attachments/assets/f5e7ad25-dfe7-472e-90e2-dff250caf930" />


