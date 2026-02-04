# SKILL 长篇小说生成器

一个纯前端的长篇小说策划/生成页面，支持配置自有大模型 API，一键生成大纲、人物档案或章节预览，并直接复制或下载 Markdown 输出。

## 功能特点
- API 可配：在页面填写 API 域名、模型 ID、API Key，默认面向类 OpenAI Chat Completion 协议。
- 参数化生成：支持题材、主角设定/性格、章节数、基调、反派与补充要求等多维度输入。
- 多种输出：可切换生成大纲、人物档案或第 1 章预览，带实时状态提示与错误高亮。
- 结果处理：输出区域支持复制、按 `{作品名}-{类型}.md` 下载；生成时带可取消的 Loading 及轮播小故事。
- 快捷作品列表：预置示例作品名，可自定义新增并一键填充。

## 快速开始
1) 本地打开：直接在浏览器打开 `index.html` 即可；若遇到浏览器本地文件限制，可在仓库根目录运行 `python3 -m http.server 8000` 后访问 `http://localhost:8000/`。
2) 填写 API：依次输入 API 域名、模型 ID、API Key、作品名。未填项会被标红并阻止请求。
3) 设定作品：选择生成类型（大纲/人物档案/章节预览），配置题材、主角设定、性格、章节数、基调，并补充反派或额外要求。
4) 生成与导出：点击「一键生成」，等待返回 Markdown，随后可复制或下载文件。

### API 约定
- 接口需允许浏览器跨域访问（CORS）。
- 请求体示例：
  ```json
  {
    "model": "Doubao-Seed-1.8",
    "messages": [
      { "role": "system", "content": "你是严谨的小说写作助手，输出 Markdown，不加代码围栏。" },
      { "role": "user", "content": "<构造的提示词>" }
    ],
    "temperature": 0.7,
    "stream": false
  }
  ```
- 返回需兼容 OpenAI 风格的字段：`choices[0].message.content`。

## 目录说明
- `index.html`：主界面与交互逻辑，包含表单、状态提示、加载遮罩、小故事轮播、输出/下载等功能。
- `SKILL.md`：长篇小说创作的流程 Skill 定义，涵盖需求收集、规划、逐章写作与质量检查步骤。
- `references/`：写作参考与模板合集（章节模板、人物模板、剧情结构、对话/钩子技巧、质量检查等）。
- `novels/`：预留的作品输出目录（当前为空，可按需存放生成的 Markdown）。
- `favioce.png` / `novelist.png`：页面使用的图标资源。

## 写作参考速览
- `references/chapter-template.md`：单章写作模板，含概要、正文与伏笔记录位。
- `references/outline-template.md`：整书大纲与章节进度表，附 TODO/进行中/已完成分区。
- `references/character-template.md` & `references/character-building.md`：人物设定模板与塑造指南。
- `references/plot-structures.md`、`references/hook-techniques.md`、`references/dialogue-writing.md`：常用叙事结构、开头钩子与对话技巧。
- `references/consistency.md`、`references/quality-checklist.md`、`references/content-expansion.md`：连贯性核查、交付前质检和扩写指引。

## 许可证

MIT，详见 `LICENSE`。
