---
title: "API 清晰性 / API Clarity"
date: "2025-01-05"
tags: ["API", "Design"]
hideMeta: false
searchHidden: false
ShowBreadCrumbs: false
---
## 命名是一种承诺
好的 API 需要 predictable naming。比如 `listUsers` 比 `getUsers` 更清楚语义。

## 混排示例
当你写 response schema 时，记得把 error code 和 message 拆开，这样更可检索。It also helps i18n.

### Code
```ts
type ApiError = { code: string; message: string };
```

```python
def format_error(code: str, message: str) -> dict:
    return {"code": code, "message": message}
```

```bash
curl -s https://api.example.com/v1/users | jq '.data[0]'
```
