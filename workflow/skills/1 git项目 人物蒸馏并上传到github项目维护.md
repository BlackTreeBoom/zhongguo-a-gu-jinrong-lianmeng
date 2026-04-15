# 1 git项目 人物蒸馏并上传到github项目维护

这份文档沉淀的是“把一组研究对象或方法论整理成 Codex 可加载 skills，并发布到 GitHub”的通用流程。它不是本次人物蒸馏任务的复盘，而是以后做同类仓库时可以直接照着执行的工作流。

## 目标

把零散资料整理成一个可维护、可引用、可发布的 skill 仓库。最终产物通常包括：

- `README.md`：说明仓库定位、收录内容、使用原则和风险边界。
- `assets/cover.svg`：用于 GitHub README 的封面。
- `skills/<skill-name>/SKILL.md`：Codex 可加载的主 skill。
- `skills/<skill-name>/references/profile.md`：公开画像、方法论抽取和常见盲区。
- `skills/<skill-name>/references/sources.md`：公开来源、链接和来源边界说明。

## 执行步骤

1. 确认 GitHub 状态。
   运行 `gh auth status`、`git status --short --branch`、`git remote -v`，先确认账号、分支、远端和工作区是否干净。

2. 明确仓库命名。
   如果仓库名不符合预期，用 `gh repo rename <新仓库名>` 修改 GitHub 地址，并用 `git remote set-url origin <新地址>` 同步本地远端。

3. 建立目录规范。
   每个 skill 单独一个目录，主文件叫 `SKILL.md`，资料放进 `references/`。不要把资料散落在根目录，也不要把同名目录重复嵌套。

4. 收集资料。
   优先使用公开可访问网页、官方页面、公开视频页、公开搜索索引和经典书籍/演讲入口。遇到反爬、登录墙或风控平台时，只记录可公开访问的信息，不绕过限制。

5. 抽取方法论。
   不要只写人物简介。每个 skill 至少要回答：何时使用、先读什么、分析顺序、输出格式、风格要求、不该怎么用。

6. 写清风险边界。
   对金融、医疗、法律等高风险领域，要明确“不是投资建议”“需独立验证”“公开摘要可能缺少上下文”等边界。

7. 更新封面和 README。
   README 顶部放封面图，正文说明仓库用途、skill 列表、使用原则、目录结构和复用方式。封面可以用 SVG，便于版本控制。

8. 本地验证。
   用 `find skills -maxdepth 3 -type f | sort` 检查目录结构，用 `git diff --stat` 检查改动范围，用 `git status` 确认没有误加临时文件。

9. 提交并推送。
   用清晰提交信息，例如 `Update skill repository presentation`。推送前如果远端拒绝，先 `git fetch origin` 对比历史，避免直接覆盖远端内容。

## 质量清单

- 每个 skill 都能落到具体分析动作，而不是人物口号。
- 每个结论都回到独立验证，不把公开大 V 观点当事实。
- 来源文件只做出处和边界说明，不堆长篇转载。
- README 能让陌生人 30 秒内看懂仓库用途。
- GitHub 地址、仓库名、封面、目录结构保持一致。

## 常用命令

```bash
gh auth status
gh repo view --json nameWithOwner,url,defaultBranchRef
gh repo rename <新仓库名>
git remote set-url origin <新仓库地址>
git status --short --branch
find skills -maxdepth 3 -type f | sort
git add README.md assets/cover.svg skills workflow
git commit -m "Update skill repository presentation"
git push -u origin main
```

## 推荐原则

先搭结构，再补内容；先讲边界，再讲观点；先验证远端，再推送。这样未来无论是金融研究、人物方法论、行业资料库，还是其他主题的 skill 仓库，都能快速复用同一套流程。
