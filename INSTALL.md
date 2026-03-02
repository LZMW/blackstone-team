# Blackstone Protocol 安装指南

本文档详细说明如何安装和配置 Blackstone 团队。

---

## 📋 前置要求

- Claude Code CLI 已安装
- 有权限访问 Claude Code 配置目录

---

## 🚀 快速安装

### 步骤 1：确定 Claude Code 配置目录

根据您的操作系统，Claude Code 配置目录位于：

| 操作系统 | 配置目录 |
|----------|----------|
| Windows | `C:\Users\{用户名}\.claude\` |
| macOS | `~/.claude/` |
| Linux | `~/.claude/` |

以下以 Windows 为例，用户名为 `Mr.Chen`：

```powershell
$CLAUDE_DIR = "C:\Users\Mr.Chen\.claude"
```

### 步骤 2：安装协调器 Skill

将协调器 skill 复制到 Claude Code skills 目录：

```powershell
# 创建目标目录
mkdir -Force "$CLAUDE_DIR\skills\blackstone-coordinator"

# 复制 skill.md
copy "blackstone-team\skills\blackstone-coordinator\skill.md" "$CLAUDE_DIR\skills\blackstone-coordinator\skill.md"
```

### 步骤 3：安装专家 Agent

将所有专家 agent 配置复制到 Claude Code agents 目录：

```powershell
# 确保 agents 目录存在
mkdir -Force "$CLAUDE_DIR\agents"

# 复制所有 agent 配置
copy "blackstone-team\agents\blackstone-zero.md" "$CLAUDE_DIR\agents\blackstone-zero.md"
copy "blackstone-team\agents\blackstone-vanguard.md" "$CLAUDE_DIR\agents\blackstone-vanguard.md"
copy "blackstone-team\agents\blackstone-nemesis.md" "$CLAUDE_DIR\agents\blackstone-nemesis.md"
copy "blackstone-team\agents\blackstone-chronos.md" "$CLAUDE_DIR\agents\blackstone-chronos.md"
```

### 步骤 4：验证安装

重启 Claude Code 后，验证安装是否成功：

```
/blackstone-coordinator 测试
```

如果协调器正确响应，说明安装成功。

---

## 📁 安装后的目录结构

```
C:\Users\Mr.Chen\.claude\
├── agents/
│   ├── blackstone-zero.md
│   ├── blackstone-vanguard.md
│   ├── blackstone-nemesis.md
│   └── blackstone-chronos.md
└── skills/
    └── blackstone-coordinator/
        └── skill.md
```

---

## 🔧 一键安装脚本

### Windows PowerShell

```powershell
# 设置源目录和目标目录
$SOURCE_DIR = "N:\编程备份4.0团队\blackstone-team"
$CLAUDE_DIR = "$env:USERPROFILE\.claude"

# 创建目标目录
New-Item -ItemType Directory -Force -Path "$CLAUDE_DIR\skills\blackstone-coordinator"
New-Item -ItemType Directory -Force -Path "$CLAUDE_DIR\agents"

# 复制协调器
Copy-Item "$SOURCE_DIR\skills\blackstone-coordinator\skill.md" "$CLAUDE_DIR\skills\blackstone-coordinator\skill.md" -Force

# 复制专家
Copy-Item "$SOURCE_DIR\agents\blackstone-zero.md" "$CLAUDE_DIR\agents\blackstone-zero.md" -Force
Copy-Item "$SOURCE_DIR\agents\blackstone-vanguard.md" "$CLAUDE_DIR\agents\blackstone-vanguard.md" -Force
Copy-Item "$SOURCE_DIR\agents\blackstone-nemesis.md" "$CLAUDE_DIR\agents\blackstone-nemesis.md" -Force
Copy-Item "$SOURCE_DIR\agents\blackstone-chronos.md" "$CLAUDE_DIR\agents\blackstone-chronos.md" -Force

Write-Host "Blackstone Protocol 安装完成！" -ForegroundColor Green
Write-Host "请重启 Claude Code 以生效。" -ForegroundColor Yellow
```

### macOS / Linux

```bash
# 设置源目录和目标目录
SOURCE_DIR="/path/to/blackstone-team"
CLAUDE_DIR="$HOME/.claude"

# 创建目标目录
mkdir -p "$CLAUDE_DIR/skills/blackstone-coordinator"
mkdir -p "$CLAUDE_DIR/agents"

# 复制协调器
cp "$SOURCE_DIR/skills/blackstone-coordinator/skill.md" "$CLAUDE_DIR/skills/blackstone-coordinator/skill.md"

# 复制专家
cp "$SOURCE_DIR/agents/blackstone-zero.md" "$CLAUDE_DIR/agents/blackstone-zero.md"
cp "$SOURCE_DIR/agents/blackstone-vanguard.md" "$CLAUDE_DIR/agents/blackstone-vanguard.md"
cp "$SOURCE_DIR/agents/blackstone-nemesis.md" "$CLAUDE_DIR/agents/blackstone-nemesis.md"
cp "$SOURCE_DIR/agents/blackstone-chronos.md" "$CLAUDE_DIR/agents/blackstone-chronos.md"

echo "Blackstone Protocol 安装完成！"
echo "请重启 Claude Code 以生效。"
```

---

## ⚙️ 配置说明

### Agent 配置文件

每个 agent 配置文件包含以下字段：

| 字段 | 说明 |
|------|------|
| `name` | Agent 名称，用于 Task 工具调用 |
| `description` | Agent 描述，用于触发识别 |
| `tools` | 可用工具列表 |
| `model` | 使用的模型（sonnet/opus/haiku） |
| `color` | 颜色标识 |

### Skill 配置文件

Skill 配置文件包含以下字段：

| 字段 | 说明 |
|------|------|
| `name` | Skill 名称，用于斜杠命令 |
| `description` | Skill 描述，用于触发识别 |

---

## 🔄 更新/卸载

### 更新

重新执行安装步骤即可覆盖更新。

### 卸载

删除相关文件：

```powershell
# 删除协调器
Remove-Item "$CLAUDE_DIR\skills\blackstone-coordinator" -Recurse -Force

# 删除专家
Remove-Item "$CLAUDE_DIR\agents\blackstone-zero.md" -Force
Remove-Item "$CLAUDE_DIR\agents\blackstone-vanguard.md" -Force
Remove-Item "$CLAUDE_DIR\agents\blackstone-nemesis.md" -Force
Remove-Item "$CLAUDE_DIR\agents\blackstone-chronos.md" -Force
```

---

## ❓ 常见问题

### Q1: 安装后无法触发协调器？

确认：
1. 文件已复制到正确位置
2. 已重启 Claude Code
3. skill.md 文件格式正确（以 `---` 开头和结尾）

### Q2: 专家无法被触发？

确认：
1. agent 配置文件已复制到 `agents/` 目录
2. description 格式正确（包含 `<example>` 标签）

### Q3: 如何验证安装成功？

使用斜杠命令测试：
```
/blackstone-coordinator 测试
```

---

## 📞 支持

如有问题，请检查：
1. Claude Code 版本是否最新
2. 配置文件格式是否正确
3. 文件路径是否正确
