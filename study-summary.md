# GitHub MCP 学习总结

## 本次实践收获

1. **MCP 是什么**：Model Context Protocol 让 AI 客户端能通过标准工具接口连接外部服务（如 GitHub）。
2. **读能力**：可用 `get_file_contents` 等工具读取仓库文件与目录。
3. **写能力**：可用 `create_or_update_file` 把内容提交回仓库，相当于完成文档更新。

## 作业对照

| 原语雀任务 | GitHub MCP 对应 |
|-----------|----------------|
| resolve_url / doc_detail | get_file_contents |
| doc_update / doc_create | create_or_update_file |

## 小结

接入 GitHub MCP 后，AI 既能「读」仓库内容做总结，也能「写」文件并在 GitHub 页面上看到改动，满足实践作业的验收要求。
