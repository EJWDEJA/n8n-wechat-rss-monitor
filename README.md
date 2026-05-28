# 基于 n8n 的全自动电商线报监控与聚合推送系统

这是一个基于低代码流水线引擎 **n8n** 搭建的云端全自动羊毛、特价线报监控系统。系统实现秒级轮询，并对异构数据进行清洗聚合，最终实现精准的高时效性企业微信富文本卡片推送。

## 🚀 核心架构与功能特性
- **数据源高频轮询**：基于 `Interval Trigger` 实现对特定电商 RSS 订阅源的秒级高频监控。
- **高性能数据瘦身**：利用 `Item Lists` 机制实现高并发流数据的批量截取，降低内存占用。
- **智能数据清洗（JS 引擎）**：在 `Code` 节点内深度嵌入 **JavaScript 核心清洗逻辑（正则表达式）**，对商品标题进行关键字过滤（如神价、手慢无），实现信息分级与垃圾垃圾垃圾过滤。
- **多条件解耦路由**：通过 `If` 条件分支节点实施增量放行控制，避免信息轰炸。
- **异构 API 深度适配**：魔改 `HTTP Request` 中的 Body 结构，实现异构多维 JSON 与企业微信 Webhook API 的完美格式适配，支持 Markdown 富文本、高亮标签及安全超链接跳转。

## 🛠 技术栈
- **Workflow Engine**: n8n
- **Data Format**: JSON / Cross-Platform API
- **Scripting Language**: JavaScript (Regex / Logic Clean)
- **Target Platform API**: WorkWeChat Webhook (Markdown Card)

## 📦 如何部署与使用
1. 下载本项目中的 `workflow.json` 文件。
2. 在你的 n8n 面板中新建一个空白工作流（Workflow）。
3. 直接在画布空白处按 `Ctrl + V`，即可一键导入完整的节点拓扑图。
4. 将 `HTTP Request` 节点的 URL 修改为您个人的企业微信机器人 Webhook 地址即可上线运行。
