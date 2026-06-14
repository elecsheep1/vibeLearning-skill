# vibeLearning-skill
> 一个科目无关的通用 AI 学习辅导引擎。

最近在准备考研复习，利用AI顺手做了一个帮助自己整理错题和总结知识的 Skill。可能还不太成熟。如果你也在用 Claude Code，欢迎试用和反馈～

## ✨ 主要功能

- **科目无关，动态加载**：只需一个配置文件，就能让 AI 掌握任意学科的教学风格。
- **三种学习模式**：
  - `exam` – 考试模式：错题诊断、输出复习卡片 + 思维导图、生成变式题
  - `professional` – 工程模式：代码调试、项目引导、架构建议
  - `research` – 研究模式：概念辨析、论文解读、开放思考题
- **错题自动分析**：上传印刷体题目图片，AI 会定位错误步骤、分类错误类型、分析根因并给出改进建议。
- **配置自进化**：遇到新错误时，AI 会主动询问是否生成配置片段，你只需复制粘贴就能让“错题库”越来越聪明。
- **支持图片输入**（推荐）和文本输入。

## 📦 安装

1. 将本仓库克隆到 Claude Code 的 skills 目录：

```
git clone https://github.com/yourname/vibe-learning-skill.git ~/.claude/skills/vibe-learning-skill
```



1. 重启 Claude Code（或输入 `/skills` 刷新列表）。
2. 为你想学习的科目创建配置文件（参考 `subjects/高等数学.md` 示例）。

## 🚀 快速使用

详细的使用教程请参考：[USER_GUIDE](./USER_GUIDE.md)

## 📁 文件结构

```
vibe-learning-skill/
├── SKILL.md              # 核心引擎（不要改动）
├── subjects/             # 科目配置文件夹
│   ├── 高等数学.md       # 示例（exam 模式）
│   ├── 规控.md           # 示例（professional 模式）
│   └── 感知.md           # 示例（research 模式）
├── templates/            # 输出模板（可选）
└── README.md
```

## ⚙️ 配置文件格式（极简）

```
# 科目名称

## 元信息
- learning_mode: exam | professional | research | general
- description: 一句话描述

## 常见错误类型分类
- 错误名称：描述、典型表现、纠正方法

## 诊断规则
- 用户出现 X → 判定为 Y 错误

## 知识点关联图
- 知识点A → 前置：[B] → 后续：[C]
```



更完整的例子请参考 `subjects/高等数学.md`。

## 🤝 贡献

由于我个人时间精力有限（复习ing），非常欢迎你：

- 提 Issue 反馈 bug 或建议
- 提交 Pull Request 改善配置模板、增加新科目的配置文件
- 分享你的使用心得

## 📄 许可证

MIT License – 随便用，如果能帮到你我会很高兴。

------

**最后说一句**：这个 Skill 是我在考研间隙写的，肯定有很多不足。如果你遇到奇怪的行为，或者有更好的想法，请一定告诉我。祝学习顺利，考研/工作/科研都上岸！ 🚀
