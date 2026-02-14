# Blackstone（黑石协议）- 安装指南

## 前置条件

- Claude Code CLI 已安装
- 配置目录: `~/.claude/` (Windows: `C:\Users\[用户名]\.claude\`)

## 自动安装（已完成）

团队配置文件已自动安装到以下位置：

```
C:\Users\29493\.claude\
├── agents\
│   ├── blackstone-chronos.md      ✅ 已安装
│   ├── blackstone-zero.md         ✅ 已安装
│   ├── blackstone-vanguard.md     ✅ 已安装
│   └── blackstone-nemesis.md      ✅ 已安装
└── skills\
    └── blackstone-coordinator\
        └── skill.md               ✅ 已安装
```

## 手动安装（如需在其他机器安装）

### 步骤1: 复制 Agents

```bash
# Windows (Git Bash)
cp -r blackstone-team/agents/*.md ~/.claude/agents/

# macOS / Linux
cp -r blackstone-team/agents/*.md ~/.claude/agents/
```

### 步骤2: 复制 Skills

```bash
# Windows (Git Bash)
cp -r blackstone-team/skills/blackstone-coordinator ~/.claude/skills/

# macOS / Linux
cp -r blackstone-team/skills/blackstone-coordinator ~/.claude/skills/
```

### 步骤3: 重启 Claude Code

```bash
# 重启 Claude Code CLI
claude
```

## 验证安装

### 方法1: 检查文件存在

```bash
# 检查 agents
ls ~/.claude/agents/blackstone-*.md

# 检查 skills
ls ~/.claude/skills/blackstone-coordinator/skill.md
```

### 方法2: 测试触发

在 Claude Code 中输入以下命令测试：

```
# 测试协调器
/blackstone-coordinator 帮我设计一个防弹级的 API 接口

# 测试专家
使用 blackstone-zero 来分析这个架构
使用 blackstone-vanguard 来添加防御性代码
使用 blackstone-nemesis 来测试这个系统
使用 blackstone-chronos 来记录技术决策
```

## 触发关键词速查

### 协调器触发词
- "防弹级代码"、"生产级"、"零熵增"
- "高复杂度"、"核心业务"、"攻坚"

### Chronos 触发词
- "技术决策"、"ADR"、"技术债务"
- "文档"、"归档"、"检查清单"

### Zero 触发词
- "架构设计"、"设计模式"、"DDD"
- "解耦"、"熵减"、"复杂度"

### Vanguard 触发词
- "防御性编程"、"熔断"、"降级"
- "输入验证"、"异常处理"

### Nemesis 触发词
- "黑盒测试"、"混沌工程"、"压力测试"
- "攻击测试"、"边界测试"

## 卸载

如需卸载，删除以下文件：

```bash
# 删除 agents
rm ~/.claude/agents/blackstone-*.md

# 删除 skills
rm -rf ~/.claude/skills/blackstone-coordinator
```

## 故障排除

### Q: 触发关键词不生效？
A: 确保文件已正确放置在配置目录，并重启 Claude Code。

### Q: 专家没有按预期响应？
A: 检查 agent 文件的 YAML frontmatter 格式是否正确。

### Q: 协调器没有触发专家？
A: 协调器需要明确的任务描述，尝试使用更具体的触发词。

## 版本信息

- 团队名称: Blackstone（黑石协议）
- 版本: 1.0.0
- 创建日期: 2026-02-14
- 专家数量: 4位
