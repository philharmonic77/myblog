---
title: "日志设计小记 / Log Design Notes"
date: "2025-01-04"
tags: ["Logging", "Design"]
hideMeta: false
searchHidden: false
ShowBreadCrumbs: false
---
## 为什么日志需要结构化
日志不是“堆文字”，而是可查询的数据。Structured logs make debugging faster, because you can filter by requestId, userId, or error code.

## Mixed 中英混排
当我们说 log schema 时，最好先定义 fields：level, message, context, traceId。Otherwise the logs become noise.

### 示例
```json
{"level":"info","message":"order created","orderId":"o_123","traceId":"t_456"}
```
