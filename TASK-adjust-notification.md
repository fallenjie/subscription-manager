# TASK: 去掉飞书推送，调整为钱包消息提醒

## 状态
DOING

## 需求来源
用户需求：订阅管理去掉飞书推送，调整为钱包消息提醒

## 需求变更说明
- **原设计**：H5 页面 + 飞书机器人推送（调用飞书 API）
- **新设计**：H5 页面（嵌入钱包）+ 钱包消息中心推送
- 核心变化：去掉飞书 API 相关代码，H5 调用钱包 SDK 的 `notify()` 方法触发钱包消息中心推送

## 变更范围
1. 去掉飞书 API 调用代码
2. 去掉 reminder_log 表的 feishu_msg_id 字段
3. 新增钱包 SDK 集成（调用 `wallet.notify()` 方法）
4. 更新 PRD 文档

## 技术方案
- 保留提醒调度逻辑（计算剩余天数、筛选待提醒订阅）
- 将飞书 API 调用替换为钱包 SDK 调用
- 钱包 SDK 接口：`wallet.notify({ title, content, subscription_id, amount, next_date })`

## 输出
- 更新后的 index.html
- 更新的 PRD（飞书文档）

## 创建时间
2026-04-15
