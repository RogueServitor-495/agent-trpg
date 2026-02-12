# TRPG 存档系统

## 存档位置

所有游戏存档保存在 `saves/` 目录下，可使用 Git 进行版本管理。

## 存档文件命名规范

```
save-{序号}-{章节简述}.json
```

示例：
- `save-001-chapter1-complete.json` - 第一章完成
- `save-002-chapter2-progress.json` - 第二章进行中

## 存档内容结构

```json
{
  "save_info": {...},      // 存档元信息
  "player_character": {...}, // 玩家角色状态
  "companions": {...},      // 队友状态
  "npcs": {...},          // NPC状态和关系
  "quests": {...},        // 任务进度
  "clues_discovered": [], // 已发现线索
  "decisions_made": [],   // 重要决策记录
  "world_state": {...},   // 世界状态
  "game_log": []         // 游戏日志
}
```

## 使用 Git 管理存档

### 初始化 Git 仓库（首次）

```bash
cd D:/dev/personal/agent-teams/.claude
git init
git add saves/
git commit -m "feat: 添加第一章存档"
```

### 创建新分支（可选）

```bash
git checkout -b save/chapter1
```

### 保存新进度

```bash
# 添加新存档
git add saves/save-*.json

# 提交
git commit -m "save: 第二章进度 - 到达安全屋"
```

### 查看存档历史

```bash
git log --oneline saves/
```

### 恢复到之前的存档

```bash
# 查看特定存档内容
git show HEAD:saves/save-001-chapter1-complete.json

# 恢复到特定提交
git checkout <commit-hash> -- saves/
```

## GM 操作指南

### 创建新存档

1. 更新 `saves/save-XXX.json` 文件
2. 更新 `save_info.save_time` 为当前时间
3. 更新所有角色和世界状态
4. 更新 `game_log` 记录最新事件

### 加载存档

1. 读取存档文件内容
2. 向玩家概述存档状态
3. 询问是否从该存档继续

### 分支存档（不同选择路线）

建议为不同剧情分支创建不同存档：

```bash
# 主线存档
saves/save-001-main.json

# 分支A存档
saves/save-001-branchA.json

# 分支B存档
saves/save-001-branchB.json
```

## 存档版本管理建议

### 主分支策略

```
main (主剧情线)
├── chapter1/
├── chapter2/
└── chapter3/

branches (不同选择)
├── peaceful-route/     # 和平路线
├── combat-route/      # 战斗路线
└── solo-route/       # 独自行动路线
```

### 提交信息规范

```
save: [章节] [描述]

示例：
- save: 第一章完成 - 天穹空间站撤离
- save: 第二章进行中 - 抵达安全屋
- save: 重要决策 - 与艾瑞斯建立同盟
```

## 当前存档列表

| 存档ID | 名称 | 章节 | 时间 |
|---------|------|------|------|
| save-001 | 第一章完成 | 天穹空间站 | 2025-02-12 |

---

**提示**：定期提交存档到 Git，避免丢失进度。不同剧情分支可以使用不同分支管理。
