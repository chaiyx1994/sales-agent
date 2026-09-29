# ernest-sales-agent

练手用的 LangChain4j + Spring Boot 项目。AI 帮你查销售数据，省得自己写 SQL。

## 跑起来

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
mvn spring-boot:run
```

端口 8087。必须 Java 21，不然 Lombok 不干活。

H2 内存库，启动自动建表插数据，不用装 MySQL。

## 接口

- `POST /api/chat` — 聊天
- `GET /api/chat/stream` — 流式
- `GET /api/tools/*` — 直接调工具

## 目录

```
agent/     AI 的接口定义和系统提示词
tool/      给 AI 用的工具
service/   查数据库的逻辑
controller HTTP 接口
config/    配置
```

## 一些事

- Redis 可选，`app.redis-enabled: true` 才开
- 权限自动裁剪：销售看自己、主管看大区、总监全看
- 时间理解靠系统提示词里的"今天是 {{today}}"，LLM 自己换算
- API Key 明文放 yml 里了，别推公共仓库

## 没做完

- 鉴权没联调
- 没前端
