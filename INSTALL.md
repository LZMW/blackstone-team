# Blackstone Team 安装指南

本指南将帮助你完成 Blackstone（黑石协议）团队的安装和配置。

## 📋 前置要求

- Claude Code 已安装并正常运行
- 对 Claude Skills 和 Agents 有基本了解
- 有访问本地文件系统的权限

## 🚀 快速安装

### 方式一：手动安装（推荐）

1. **复制配置包到用户目录**

```bash
# 复制整个 blackstone-team 文件夹到你的 Claude skills 目录
# Windows: C:\Users\[用户名]\.claude\skills\
# macOS/Linux: ~/.claude/skills/

# 复制 agents 到 agents 目录
# Windows: C:\Users\[用户名]\.claude\agents\
# macOS/Linux: ~/.claude/agents/
```

2. **验证文件结构**

确保以下文件存在：

```
# Skill（协调器）
.claude/skills/blackstone-coordinator/skill.md

# Agents（专家）
.claude/agents/blackstone-zero.md
.claude/agents/blackstone-vanguard.md
.claude/agents/blackstone-nemesis.md
.claude/agents/blackstone-chronos.md
```

3. **重启 Claude Code**

重新启动 Claude Code 以加载新配置。


应该能看到 Blackstone 协调器的帮助信息。

### 2. 测试专家 Agent

在 Claude Code 中尝试：

```
使用 blackstone-zero 子代理执行一个简单的架构设计任务
```

应该能看到 Zero 架构师开始工作。

## 📁 文件结构说明

```
blackstone-team/
├── README.md                          # 本文件
├── INSTALL.md                         # 安装指南
├── agents/                            # 专家 Agent 配置
│   ├── blackstone-chronos.md          # 资产总管
│   ├── blackstone-zero.md             # 多维架构师
│   ├── blackstone-vanguard.md         # 铁壁编码者
│   └── blackstone-nemesis.md          # 黑盒破坏者
└── skills/                            # 协调器 Skill
    └── blackstone-coordinator/
        └── skill.md                   # 协调器
```

## 🔧 配置说明

### 协调器 (blackstone-coordinator)

- **文件位置**: `skills/blackstone-coordinator/skill.md`
- **触发方式**: `/blackstone-coordinator [任务描述]`
- **核心职责**: 任务规划、专家协调、结果汇总

### 专家 Agents

| 代号 | 文件名 | 核心职责 | MCP工具 |
|------|--------|----------|---------|
| Zero | blackstone-zero.md | 架构设计、熵减 | sequential-thinking, context7 |
| Vanguard | blackstone-vanguard.md | 防御编码、熔断器 | context7 |
| Nemesis | blackstone-nemesis.md | 黑盒测试、混沌工程 | 无 |
| Chronos | blackstone-chronos.md | ADR、技术债务 | 无 |

## 📊 工作流程

```
用户请求
    ↓
协调器分析
    ↓
Need 沟通? ──Yes──→ AskUserQuestion
    ↓ No
规划流程
    ↓
Need MCP? ──Yes──→ 征求用户授权
    ↓ No
依次触发专家
    ↓
Zero → Vanguard → Nemesis → Chronos
    ↓
汇总输出
    ↓
交付用户
```

## 🎯 使用示例

### 示例1：完整流程

```
用户: /blackstone-coordinator 设计一个防弹级的支付回调接口

协调器: [需求沟通] 确认支付场景、安全要求...
协调器: [流程规划] 需要完整接力流程
协调器: [MCP授权] Zero可能需要查询架构最佳实践，是否授权？
用户: 同意授权
协调器: [触发专家] 依次触发 Zero → Vanguard → Nemesis → Chronos
协调器: [汇总输出] 生成最终交付报告
```

### 示例2：单独使用专家

```
用户: 使用 blackstone-zero 子代理设计用户认证模块的架构

Zero: [分析需求] 用户认证涉及身份验证、权限管理...
Zero: [架构设计] 采用DDD切割用户上下文...
Zero: [创建INDEX] 生成架构决策指令
```

## 🛠️ 故障排查

### 问题1：协调器无法触发

**可能原因**：
- Skill 文件未正确放置
- 文件名或路径不正确

**解决方案**：
1. 检查 `skills/blackstone-coordinator/skill.md` 是否存在
2. 确认文件名完全匹配（区分大小写）
3. 重启 Claude Code

### 问题2：专家 Agent 无法触发

**可能原因**：
- Agent 文件未正确放置
- MCP 工具未授权导致执行失败

**解决方案**：
1. 检查 `agents/blackstone-*.md` 是否存在
2. 确认协调器已正确授权 MCP 工具
3. 查看错误日志获取详细信息

### 问题3：MCP 工具无法使用

**可能原因**：
- 协调器未授权
- MCP 服务未启动

**解决方案**：
1. 确认协调器在触发指令中包含 `🔓 MCP 授权`
2. 检查 MCP 服务是否正常运行
3. 查看具体工具名称是否正确

## 📚 进一步学习

- [Claude Code 官方文档](https://docs.anthropic.com/claude-code)
- [Skills 开发指南](https://docs.anthropic.com/claude-code/skills)
- [Agents 配置参考](https://docs.anthropic.com/claude-code/agents)

## 🤝 获取帮助

如果遇到问题：

1. 查看本文档的故障排查章节
2. 检查 GitHub Issues
3. 在社区论坛提问

## 📝 更新记录

| 版本 | 日期 | 说明 |
|------|------|------|
| 3.0 | 2026-03-01 | 使用 super-team-builder v3.0 重构 |
| 2.0 | 2026-02-28 | 优化协调器和专家配置 |
| 1.0 | 2026-02-01 | 初始版本 |

---

**安装完成后，你就可以开始使用 Blackstone 团队处理高危、高复杂度的软件工程任务了！**
