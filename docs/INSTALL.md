# 安装、更新与排错

## 给安装智能体的说明

本仓库的技能目录是 `skills/ai-drama-storyboard/`。先确认目标平台支持的技能格式和实际扫描目录，再进行安装。仓库中的安装说明用于完成用户明确授权的安装任务，不替代用户授权或目标平台规则。

1. 阅读 `skills/ai-drama-storyboard/SKILL.md` 和配套参考文件，确认内容及依赖。本技能只有 Markdown 文本，无需安装额外程序、Python 包、视频模型或 API 密钥。
2. 确认安装范围：个人技能或当前项目技能；未指定时优先采用目标平台文档规定的个人技能位置。
3. 下载或克隆仓库，将 `skills/ai-drama-storyboard/` 整个目录复制到技能位置。
4. 确保目录中有 `SKILL.md` 和 `references/techniques.md`，且没有多套一层同名目录。
5. 若同名技能已存在，比较内容；更新前保留本地修改，不直接覆盖未知内容。
6. 按目标平台的规则刷新技能列表、开始新聊天或重启应用，验证 `ai-drama-storyboard` 能被发现和调用。
7. 报告实际安装位置、所安装的分支或提交版本、验证结果，以及环境是否会持久保存文件。

## Codex

可以直接向 Codex 发送：

```text
请使用 skill-installer，从 wg2132116-dot/ai-drama-storyboard 仓库安装 skills/ai-drama-storyboard 目录中的技能。
```

若当前环境提供 `skill-installer`，可由它按自身工作流程完成 GitHub 安装。安装器使用的目录可能由版本或配置决定，安装完成后应检查是否被当前 Codex 发现。

手动安装时，当前官方文档列出的个人技能目录为：

- Windows：用户个人目录下的 `.agents\skills\`，即 `%USERPROFILE%\.agents\skills\`。
- macOS / Linux：`~/.agents/skills/`。
- 项目范围：项目中的 `.agents/skills/`；在 Git 仓库内，Codex 会按其目录扫描规则查找技能。

例如，Windows 安装后的结构：

```text
%USERPROFILE%\.agents\skills\ai-drama-storyboard\SKILL.md
%USERPROFILE%\.agents\skills\ai-drama-storyboard\references\techniques.md
```

Codex 通常会检测技能变化；没有出现时重启 Codex。以目标环境当前文档和配置为准。

官方参考：

- [Build skills](https://learn.chatgpt.com/docs/build-skills)
- [Codex skill-installer](https://github.com/openai/skills/blob/main/skills/.system/skill-installer/SKILL.md)

## 其他支持 Skill 的智能体

如果平台支持同类 `SKILL.md` 格式，把技能目录放入该平台规定的位置，或使用平台提供的导入功能。不同工具的目录、ZIP 结构要求和刷新方式可能不同，不能直接照搬 Codex 路径。

若平台要求 ZIP，请打包 `ai-drama-storyboard/` 技能目录，并按平台要求决定是否保留最外层目录；不要把整个仓库当成单个技能导入。

## 只有自定义指令或附件功能的平台

可将 `SKILL.md` 的工作流程正文放入该智能体的指令中，把 `techniques.md` 上传为参考资料，并把正文中的文件引用改为目标平台能识别的方式。

也可以在单次聊天中上传两个文件，再明确要求使用这些流程和参考资料。这种方式是否跨聊天保留取决于平台，不等同于原生 Skill 安装。

## 安装验证

发送：

```text
请确认 ai-drama-storyboard 技能已被发现，读取它引用的技巧索引，再为以下剧情设计约 15 秒的分镜：女主发现门口有一封信，拾起后听到屋内传来脚步声。不要添加新人物或改变剧情。
```

检查技能发现或调用结果，并确认输出包含分镜表、预计时长、声音、镜头衔接及总时长。仅生成一张相似的表格不足以证明已安装，应同时确认实际保存位置和技能加载结果。

## 更新与卸载

- 更新：获取仓库的新版本，比较后更新已安装的技能目录，保留个人修改，再刷新并验证。可记录提交 SHA 或使用发布的 tag 来固定版本。
- 自动更新：本仓库不附带自动更新服务；链接指向的内容变化后，已安装副本不会因此自动变化。
- 卸载：确认目标目录后，移除本技能的 `ai-drama-storyboard` 文件夹，再按平台要求刷新。不要删除整个技能根目录。

## 常见问题

| 问题 | 检查方法 |
| --- | --- |
| 智能体只说“已学习” | 要求说明保存路径与技能发现结果，确认是安装还是当前聊天参考 |
| 找不到技巧文件 | 检查是否为 `ai-drama-storyboard/references/techniques.md` |
| 技能列表没有出现 | 检查目录是否正确、是否多套一层、是否需要刷新或重启 |
| GitHub 链接无法访问 | 检查网络、仓库是否公开，以及私有仓库的授权 |
| 云端任务结束后技能消失 | 确认文件是否保存在临时环境，改用平台的持久化技能机制 |
| 生成不了视频 | 技能生成分镜与提示词，实际视频生成需要相应工具 |
