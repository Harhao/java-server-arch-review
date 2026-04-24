# 审查清单索引

各维度检查项索引。每个检查项的详细规则（检测逻辑、示例代码、修复方案）参阅对应的 `references/` 文件。

## 编码与安全

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-0001 | MAJOR | 命名规范一致性 | `coding-standards.md` |
| CHECK-0002 | MINOR | Commit Message 规范 | `coding-standards.md` |
| CHECK-0101 | BLOCKER | WHERE 条件高频字段缺少索引 | `database-index.md` |
| CHECK-0102 | MAJOR | JOIN 连接字段缺少索引 | `database-index.md` |
| CHECK-0103 | MAJOR | ORDER BY / GROUP BY 字段缺少索引 | `database-index.md` |
| CHECK-0104 | MAJOR | 联合索引未遵循最左前缀原则 | `database-index.md` |
| CHECK-0105 | MINOR | 写多读少场景的过度索引 | `database-index.md` |
| CHECK-0201 | BLOCKER | MyBatis 使用 ${} 替代 #{} | `sql-injection.md` |
| CHECK-0202 | BLOCKER | 字符串拼接 SQL | `sql-injection.md` |
| CHECK-0203 | MAJOR | 数据库账号权限过大 | `sql-injection.md` |

## 工程实践

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-0301 | BLOCKER | 敏感信息硬编码 | `config-logging.md` |
| CHECK-0302 | MAJOR | 未使用多环境配置 | `config-logging.md` |
| CHECK-0303 | MAJOR | 配置值未通过 Spring 注入 | `config-logging.md` |
| CHECK-0401 | BLOCKER | 关键业务操作缺少日志 | `config-logging.md` |
| CHECK-0402 | BLOCKER | 异常捕获后未记录日志 | `config-logging.md` |
| CHECK-0403 | MAJOR | 日志缺少上下文信息 | `config-logging.md` |
| CHECK-0404 | MAJOR | 日志级别使用不当 | `config-logging.md` |
| CHECK-0501 | BLOCKER | 缺少全局异常处理器 | `error-handling.md` |
| CHECK-0502 | BLOCKER | 5xx 错误暴露堆栈信息 | `error-handling.md` |
| CHECK-0503 | MAJOR | 缺少统一业务异常体系 | `error-handling.md` |
| CHECK-0504 | MAJOR | HTTP 状态码使用不当 | `error-handling.md` |

## 代码架构

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-0601 | BLOCKER | Controller 层包含业务逻辑 | `code-layering.md` |
| CHECK-0602 | BLOCKER | Service 层直接操作 HTTP 语义 | `code-layering.md` |
| CHECK-0603 | MAJOR | 超大 Service 类 | `code-layering.md` |
| CHECK-0604 | MINOR | 分层领域模型混用 | `code-layering.md` |
| CHECK-0701 | MAJOR | 重复代码块 | `code-layering.md` |
| CHECK-0702 | MAJOR | Magic Number / Magic String | `code-layering.md` |
| CHECK-0703 | MINOR | 重复校验逻辑未封装 | `code-layering.md` |

## 安全防护

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-0801 | BLOCKER | 接口缺少认证保护 | `security-auth.md` |
| CHECK-0802 | BLOCKER | 资源操作缺少越权检查 | `security-auth.md` |
| CHECK-0803 | MAJOR | Token/Session 方案安全性 | `security-auth.md` |
| CHECK-1001 | BLOCKER | 接口入参未校验 | `api-design.md` |
| CHECK-1002 | BLOCKER | 请求体 VO 缺少校验注解 | `api-design.md` |
| CHECK-1003 | MAJOR | 文件上传未校验类型和大小 | `api-design.md` |
| CHECK-1004 | MAJOR | 输出到前端的内容未转义 | `api-design.md` |
| CHECK-1101 | MAJOR | 公开接口缺少限流 | `rate-limiting.md` |
| CHECK-1102 | BLOCKER | 多实例部署使用本地限流 | `rate-limiting.md` |
| CHECK-1103 | MAJOR | 限流粒度不合理 | `rate-limiting.md` |
| CHECK-1104 | MAJOR | 限流算法选型不当 | `rate-limiting.md` |
| CHECK-1105 | MAJOR | 登录接口缺少暴力破解防护 | `rate-limiting.md` |
| CHECK-1106 | MAJOR | 限流触发后缺少友好响应 | `rate-limiting.md` |
| CHECK-1107 | MINOR | 敏感操作缺少二次验证 | `rate-limiting.md` |
| CHECK-1108 | MINOR | 缺少限流监控和告警 | `rate-limiting.md` |

## API 设计

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-0901 | MAJOR | URL 设计不符合 RESTful | `api-design.md` |
| CHECK-0902 | MAJOR | 响应格式不统一 | `api-design.md` |
| CHECK-0903 | MAJOR | 列表接口缺少分页 | `api-design.md` |
| CHECK-0904 | MINOR | 缺少 API 版本控制 | `api-design.md` |

## 质量保障

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-1201 | MAJOR | 缺少 README | `quality-testing.md` |
| CHECK-1202 | MAJOR | 缺少 API 接口文档 | `quality-testing.md` |
| CHECK-1203 | MINOR | 数据库变更未版本化 | `quality-testing.md` |
| CHECK-1301 | BLOCKER | 核心业务逻辑缺少单元测试 | `quality-testing.md` |
| CHECK-1302 | MAJOR | 高风险业务缺少测试覆盖 | `quality-testing.md` |
| CHECK-1303 | MAJOR | CI 流水线缺少测试门禁 | `quality-testing.md` |
| CHECK-1304 | MINOR | 测试中使用 System.out 而非 assert | `quality-testing.md` |
| CHECK-1401 | MAJOR | 缺少代码格式化/lint 配置 | `quality-testing.md` |
| CHECK-1402 | MINOR | Pull Request 流程未强制 | `quality-testing.md` |

## 数据层架构

| CHECK ID | 等级 | 检查项 | 参考文件 |
|----------|------|--------|---------|
| CHECK-2001 | BLOCKER | 数据查询缺少归属过滤 | `data-storage.md` |
| CHECK-2002 | MAJOR | 表缺少时间戳字段 | `data-storage.md` |
| CHECK-2003 | MAJOR | 未使用软删除 | `data-storage.md` |
| CHECK-2004 | MAJOR | 密码明文存储 | `data-storage.md` |
| CHECK-2101 | MAJOR | 缓存策略不当 | `data-storage.md` |
| CHECK-2102 | MAJOR | 多实例部署未考虑状态共享 | `data-storage.md` |
| CHECK-2201 | BLOCKER | 事务范围不当 | `data-storage.md` |
| CHECK-2202 | BLOCKER | 事务中 catch 异常未回滚 | `data-storage.md` |
| CHECK-2301 | BLOCKER | schema 变更无版本化管理 | `db-migration.md` |
| CHECK-2302 | BLOCKER | 迁移文件被修改 | `db-migration.md` |
| CHECK-2303 | MAJOR | 迁移文件缺少回滚方案 | `db-migration.md` |
| CHECK-2304 | MAJOR | 迁移文件命名不规范 | `db-migration.md` |
| CHECK-2305 | MAJOR | 迁移文件未纳入 Git | `db-migration.md` |
| CHECK-2306 | MINOR | 未配置迁移框架基线版本 | `db-migration.md` |
| CHECK-2401 | BLOCKER | DDL 变更未评估锁表风险 | `db-migration.md` |
| CHECK-2402 | BLOCKER | 字段变更不向后兼容 | `db-migration.md` |
| CHECK-2403 | BLOCKER | 数据订正未先 SELECT 确认 | `db-migration.md` |
| CHECK-2404 | MAJOR | 新增字段未设置合理默认值 | `db-migration.md` |
| CHECK-2405 | MAJOR | 大表变更未分批执行 | `db-migration.md` |
| CHECK-2406 | MAJOR | UPDATE 未同步更新 updated_at | `db-migration.md` |
| CHECK-2407 | MAJOR | 缺少数据库变更审批流程 | `db-migration.md` |
| CHECK-2408 | MINOR | 废弃表/字段未及时清理 | `db-migration.md` |
