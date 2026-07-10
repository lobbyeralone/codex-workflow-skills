# 推荐 Skills 中文说明

这三个 skill 建议优先安装，因为它们解决的是 AI Agent 工作中最常见、最容易造成返工的三个问题：

- 上下文和知识库分散。
- 项目专属规则误触到其他仓库。
- Agent 过早声称完成，但没有逐条证据。

## 总览

| Skill | 解决的问题 | 什么时候用 | 使用后会怎样 |
| --- | --- | --- | --- |
| `tidy-knowledge-base` | 文档、prompt、工作流、工具说明分散在多个文件里。 | 当一个目录里有太多说明文档、重复索引或过期入口时。 | 收敛成一个主知识库，模板单独存放，旧链接和私有内容被检查清理。 |
| `scope-project-skills` | 项目专属 skill 放在全局，容易在无关项目误触。 | 当某个 skill 明显只属于一个项目、仓库或业务域时。 | 项目 skill 被移动到项目本地目录，全局 skill 更干净，路由更安全。 |
| `audit-completion-evidence` | Agent 还没证明每条需求就说“完成”。 | 在任务、修复、安装、迁移、文档更新或 `/goal` 准备收尾前。 | 每条需求都有证据；证据弱或缺失时会继续补齐，而不是提前总结。 |

## 1. `tidy-knowledge-base`

### 中文含义

知识库收敛器。

它用于把分散的文档、prompt、工具笔记、工作流、Agent 规则合并成一个可维护的主知识库。

### 推荐理由

AI 辅助开发很容易越用越散：今天写一个 prompt 文件，明天写一个工具说明，后天又加一个 workflow 清单。时间久了，README 变成入口迷宫，真正有用的知识反而没人愿意读。

这个 skill 的价值是把“资料堆”整理成“可执行知识库”：

- 日常只看一个主文档。
- 模板和正文分开。
- 重复规则只保留一份。
- 旧链接、敏感信息、项目私有内容都要检查。

### 依据

这个 skill 是从一次真实知识库整理任务中抽出来的。当时多个编号文档被合并成一个集中版主文档，同时保留 README 和 templates 目录。可复用的不是具体内容，而是整理流程：

1. 盘点文件。
2. 分类主知识、模板、重复索引、过期说明、私有内容。
3. 合并可复用内容。
4. 删除重复入口。
5. 扫描旧链接和敏感信息。

### 什么场景使用

适合：

- 知识库里有很多入口文件，不知道该看哪个。
- README 链接了很多重复或过期文档。
- prompt、工具命令、工作流、Agent 规则散落在不同文件。
- 团队想沉淀 AI 使用规范，但不能泄露密钥、日志、项目路径。

不适合：

- 只有一个短 README。
- 只是想改一两句文案。
- 文档内容本身还没有形成可复用模式。

### 使用后会怎样

使用后应该得到：

- 一个主知识库文档。
- 一个简洁 README。
- 模板目录独立存在。
- 旧编号文档或重复索引被合并、删除或归档。
- 输出会说明保留了什么、删除了什么、验证了什么。

### 典型请求

```text
Use tidy-knowledge-base to merge this documentation folder into one maintainable knowledge base. Keep reusable guidance, separate templates, remove stale links and private material, then report verification results.
```

中文可以这样说：

```text
使用 tidy-knowledge-base，把这个文档目录整理成一个可维护的主知识库。保留可复用内容，模板单独放，删除旧链接和私有内容，最后报告验证结果。
```

## 2. `scope-project-skills`

### 中文含义

项目 skill 本地化器。

它用于把只适合某个项目的 skill 从全局 skill 目录移出去，放到项目自己的 `.codex-project/skills` 目录下。

### 推荐理由

全局 skill 很方便，但如果把项目专属规则也放全局，就会有误触风险。比如一个 skill 只适合某个仓库，却在其他项目里也出现在候选列表中，Agent 可能错误套用规则。

这个 skill 的价值是把“项目规则”和“通用规则”分开：

- 通用 skill 留在全局。
- 项目 skill 放回项目目录。
- 全局只保留轻量路由。
- 只有确认当前目录属于对应项目后，才加载项目规则。

### 依据

这个 skill 是从一次真实 cleanup 里抽象出来的。当时项目专属 skills 从全局目录迁移到了项目本地 `.codex-project/skills`，并更新了全局路由规则。

可复用模式是：

1. 找出全局里的项目专属 skill。
2. 确认目标项目根目录。
3. 移动到项目本地 skills 目录。
4. 更新全局路由规则。
5. 校验 skill frontmatter。
6. 确认全局不再误触。

### 什么场景使用

适合：

- 某个 skill 名称、描述或内容明显属于单一项目。
- skill 里包含项目路径、模块名、协议、业务域或私有流程。
- 全局 skill 列表太吵，容易触发错误项目规则。
- 你想开源通用 skill，但不想夹带项目专属规则。

不适合：

- skill 本来就是跨项目通用能力。
- 只是想临时禁用某个 skill。
- 项目根目录还没确认清楚。

### 使用后会怎样

使用后应该得到：

- 项目专属 skill 从全局目录消失。
- 项目目录下出现 `.codex-project/skills`。
- 全局只保留通用路由逻辑。
- Agent 在其他项目里不会再误用该项目规则。
- 输出会说明移动了哪些 skill、目标位置、验证结果和跳过原因。

### 典型请求

```text
Use scope-project-skills to move project-specific skills out of global discovery. Confirm the target repository, move them into `.codex-project/skills`, update routing, and validate the moved skills.
```

中文可以这样说：

```text
使用 scope-project-skills，把项目专属 skills 从全局发现列表移出去。先确认目标仓库，再移动到 `.codex-project/skills`，更新路由，并校验迁移后的 skills。
```

## 3. `audit-completion-evidence`

### 中文含义

完成审计。

它用于在 Agent 准备说“完成”之前，强制逐条检查用户需求是否真的被当前证据证明。

### 推荐理由

Agent 最容易犯的错误之一是提前收尾：代码改了、文档写了、命令跑了一部分，就开始说“完成”。但用户真实需求可能还有遗漏，验证也可能没有覆盖风险。

这个 skill 的价值是让“完成”变成一个可证明的结论：

- 先拆原始需求。
- 每条需求找证据。
- 证据弱就不能算完成。
- 缺口要继续补，而不是先总结。

### 依据

这个 skill 来自多次 `/goal` 和长任务收尾审计。只有在实际文件、链接扫描、敏感扫描、命令输出和用户要求都能逐条对应时，才允许标记完成。

可复用模式是：

1. 保留原始目标，不缩小范围。
2. 拆成可验证要求。
3. 为每条要求找到证据类型。
4. 检查当前文件、命令输出或运行结果。
5. 标注 proven、incomplete、weak evidence、missing evidence。
6. 有缺口就继续做。

### 什么场景使用

适合：

- 准备标记 `/goal` complete。
- Bug 修复准备收尾。
- 工具安装、迁移、配置改动完成后。
- 文档整理、知识库更新完成后。
- 用户要求“证明一下”“验收一下”“做最终检查”。

不适合：

- 用户只是问一个概念。
- 临时讨论方案，还没进入交付。
- 没有明确完成标准的闲聊。

### 使用后会怎样

使用后应该得到：

- 原始需求被拆成验收项。
- 每个验收项都有证据或缺口说明。
- 不能验证的部分会被明确标出。
- Agent 不会只凭感觉说完成。
- 如果还有缺口，Agent 会继续补齐。

### 典型请求

```text
Use audit-completion-evidence before finalizing this task. Split the original request into requirements, inspect current evidence for each one, continue on missing items, and only claim completion when every item is proven.
```

中文可以这样说：

```text
使用 audit-completion-evidence，在最终总结前做完成审计。把原始需求拆成验收项，逐条检查当前证据，缺什么继续补，只有全部被证明后才能说完成。
```

## 选择指南

| 你的问题 | 用哪个 |
| --- | --- |
| 文档、prompt、工具说明太分散，不知道看哪个。 | `tidy-knowledge-base` |
| 某个项目 skill 总是出现在无关项目里。 | `scope-project-skills` |
| Agent 说完成，但你不确定有没有证据。 | `audit-completion-evidence` |

## 安装示例

```powershell
Copy-Item -Recurse .\open-source-skills\tidy-knowledge-base $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\scope-project-skills $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\audit-completion-evidence $env:USERPROFILE\.codex\skills\
```

安装后重启 Codex。
