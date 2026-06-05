---
name: designfigma-builingbuiling
description: 高保真还原 Figma 设计稿到前端代码。Use when Codex needs to implement, translate, rebuild, or review Figma frames/nodes, Figma MCP output, UI screenshots, frontend interactions, component-library screens, cut images, SVG icons, masks, image assets, project design-system screens, or Chanquanquan-style web pages; must read precise Figma nodes, route to relevant design specs, preserve real Figma assets, avoid screenshot-based fake UI, and verify the result with browser screenshots.
---

# 设计稿还原

## 目的

在根据 Figma 设计稿实现或评审前端页面前使用这个 skill。它要求先精确读取 Figma 节点，再按需调用项目/组件库设计规范，保留真实切图和 icon 资产，最后用浏览器截图做视觉验收。

蝉圈圈组件库规范放在 `references/chanquanquan-design.md`。只有当用户、项目、仓库或 Figma 文件明确和蝉圈圈设计系统相关时才加载它。需要查规范章节时，先看 `references/index.md`。

## 工作流

1. 先读精确设计节点：
   - 必须拿到带 `node-id` 的 Figma URL，或明确的 `node-id`。如果链接没有 `node-id`，且无法从上下文确定目标节点，要让用户提供具体 frame/node 链接，不要猜。
   - 用 `get_design_context` 读取用户给的 Figma frame/node。
   - 当大 frame 结构不清楚时，用 `get_metadata` 拆到具体子节点。
   - 当颜色、字体、间距或状态值看起来由变量控制时，用 `get_variable_defs` 读取变量。
   - 如果有 Code Connect 映射，要检查映射，并优先复用已映射的项目组件，而不是从零重写。
   - 确认哪些层是 frame、component、instance、mask、vector、SVG icon、image fill、bitmap export、text layer、variable、component state。
   - 不要只根据截图猜测资产结构。

2. 导出同一节点作为视觉基准：
   - 用 `get_screenshot` 导出同一个 frame/node。
   - 这个截图只用于对比位置、尺寸、颜色、透明度、裁切、圆角、阴影和 mask。
   - Figma 截图只能作为视觉对比基线，不能作为最终 UI 实现素材。
   - 大页面里如果 icon 或 mask 图片看不清，可以额外截图关键子节点。

3. 判断并读取设计规范：
   - 先识别页面类型和可见组件，再决定要读哪些规范。
   - 如果仓库里有 `DESIGN.md`、设计 token、theme 文件、组件文档或 repo instructions，要先读项目本地规范。
   - 只有蝉圈圈相关任务，或用户明确要求使用蝉圈圈组件库时，才读取 `references/index.md` 和 `references/chanquanquan-design.md`。
   - 取值优先级：Figma 节点变量/样式 > Code Connect/项目组件 > 项目 token > 组件库 token > 语义组件规则 > 临近 token 推导。

4. 保留真实 Figma 资产：
   - 如果 Figma MCP 返回 `localhost` 图片/SVG 资源，实现和视觉对比阶段可以使用。
   - 交付前，要把需要的 Figma 资产下载到项目资产目录、`public/static` 或项目已有 asset pipeline；除非任务只是临时预览。
   - 不要让可交付代码依赖 Figma MCP 临时 `localhost` URL。
   - 不要用占位图替代已返回的资产。
   - 不要把 Figma 里的 icon 擅自换成 lucide、iconfont、emoji、项目里的相似 icon 或手写替代图标，除非用户明确允许。
   - 如果 MCP 没有返回某个资产，继续拆更细的子节点检查；如果仍然拿不到，要明确报告缺失的是哪个资产，不能静默替换。

5. 区分 SVG 和位图：
   - 矢量 icon 优先保留 SVG，并保持 `viewBox`、`fill`、`stroke`、`opacity`、mask、clip、尺寸。
   - PNG/JPG/WebP 资产要匹配 Figma 原始尺寸、裁切方式、`object-fit`、圆角、透明度和 clipping。
   - 如果 icon 颜色由设计变量控制，在项目支持时还原成 CSS/token 控制。
   - 如果 icon 是固定导出资产，就保持原图颜色。

6. 实现前端布局和交互：
   - 优先复用项目已有组件、token、theme 变量和 CSS 约定。
   - 如果有匹配的 Code Connect 组件，并且适合目标节点，优先使用它。
   - 页面、模块、卡片、导航、表单、表格、筛选区和交互区域必须用真实 DOM/CSS/组件实现。
   - 不只摆放视觉内容，还要还原 frame 尺寸、padding、alignment、constraints、object position 和响应式行为。
   - 如果项目已有 token 系统，要把组件库 token 映射进去，不要到处硬编码重复色值。
   - 业务系统页面保持克制的信息密度：浅背景、白色内容面、低对比边框、清晰表格和明确交互状态。
   - 如果临时用截图辅助定位，交付前必须移除。

7. 浏览器视觉验收：
   - 本地应用需要启动时，先启动页面并截图。
   - 对照 Figma 截图检查 icon 是否缺失、颜色是否变化、透明度/mask 是否丢失、裁切是否错误、是否拉伸、Retina/缩放下是否模糊、圆角/阴影/间距/对齐是否一致。
   - 检查实现里是否存在整页/整 section/整 card/整 navigation 截图覆盖、透明 DOM 热区、`opacity: 0` 点击层、大块 bitmap 假 UI。
   - 交付前搜索改动代码，检查是否残留临时 MCP URL、截图覆盖、整块导出 UI 图、透明热区或隐藏交互层。
   - 如果任务包含交互状态，要检查 hover、active、focus、disabled、error 等状态里的 icon 和颜色。
   - 在项目技术栈允许的范围内，迭代到浏览器截图和 Figma 截图足够接近，同时保持真实可维护的前端实现。

## 禁止截图替代实现

Figma 截图只能作为视觉对比基线，不能作为页面、模块、卡片、导航、表单、表格、筛选区等 UI 的实现素材。

禁止：

- 导出整页、整块 section、整张 card、整条 navigation、整张表格、整组表单或筛选区作为 PNG/WebP 覆盖到页面中。
- 用截图当视觉层，再用透明 DOM 或 `opacity: 0` 元素作为点击热区。
- 为了提高像素相似度，用大块位图替代可由 HTML/CSS/组件实现的界面。
- 把截图相似度放在清晰度、可维护性、可访问性和真实交互之上。

允许使用的 Figma 资产：

- 原设计中本来就是图片的内容，例如头像、商品图、视频封面、插画、背景图。
- 原设计中本来就是独立矢量/icon/logo 的 SVG 或导出资源。
- 无法用 CSS 准确表达，且设计本身定义为装饰图片的 bitmap asset。

验收要求：

- 最终页面必须主要由真实 DOM/CSS/组件构成。
- Figma screenshot 不得进入最终 UI，除非该节点本身就是图片资产。
- 临时截图定位层必须在交付前移除。
- 必须检查是否存在截图覆盖、透明热区、`opacity: 0` 交互层。
- 视觉相似度目标不得通过截图覆盖达成。

## 设计规范路由

先读取项目本地设计规则，例如 `DESIGN.md`、设计 token、theme 文件、组件文档或仓库指令。只有当任务属于蝉圈圈组件库，或用户明确要求使用蝉圈圈规范时，才加载蝉圈圈参考文档。

蝉圈圈相关任务按需读取 `references/chanquanquan-design.md`：

- 品牌气质和整体风格：章节 `1` 和 `7`。
- 颜色、token 匹配、状态色：章节 `2`、`6.1`、`6.2`。
- 字体：章节 `3` 和 `6.4`。
- 按钮、卡片、数据卡、导航、表格、表单、标签、图表、Banner：对应 `4.x` 章节。
- 页面布局和缺失 token 的兜底规则：章节 `5`。
- 渐变：章节 `2.5` 和 `6.3`。
- 当前规范缺失、需要从 Figma 节点推导的内容：章节 `8`。

优先用 `rg` 搜索引用资料：

```bash
rg -n "按钮|Button|表格|Table|表单|Form|标签|Badge|Tag|图表|Chart|渐变|Typography|字体|Token|颜色匹配|切图|icon|SVG|mask" references
```

## 代码检查

非简单还原任务交付前，要检查改动过的前端代码里是否存在反模式：

```bash
rg -n "localhost:|127\\.0\\.0\\.1|figma|screenshot|opacity:\\s*0|pointer-events|position:\\s*absolute|<img|background-image|data:image|png|webp|jpg|jpeg|svg" .
```

检查结果要结合上下文判断：

- 临时 Figma MCP `localhost` URL 不能留在可交付代码里。
- 大块 `<img>` 或 `background-image` UI 很可疑，除非源节点本身确实是图片资产。
- `opacity: 0`、透明覆盖层、`pointer-events` 交互层必须有明确理由。
- `position: absolute` 可以用于忠实还原布局，但不能用来把透明热区盖在假 UI 截图上。

## 资产验收清单

交付前明确检查：

- Figma 提供的图片和 SVG 资产都出现在实现里。
- 设计稿提供的 icon 没有被其他 icon 库擅自替换。
- SVG 的 `viewBox`、`fill`、`stroke`、`opacity`、mask、clip path、尺寸没有丢。
- 位图资产匹配 Figma 的裁切、`object-fit`、圆角和显示尺寸。
- icon 颜色仍然符合固定资产或变量/token 控制逻辑。
- icon 在浏览器/设备缩放下保持清晰。
- hover、active、disabled、focus、selected、loading、empty、error 等状态使用正确的 icon 或资产变体。

## 硬性约束

- 不要在规范有相近 token 时发明新品牌色。
- 不要把蝉圈圈品牌 token 套到无关项目上，除非用户或仓库上下文明确要求使用这个设计系统。
- 不要用通用规范默认值覆盖 Figma 组件上的精确值。
- 不要把临时 Figma MCP `localhost` 资产 URL 留在交付代码中。
- Figma MCP 节点数据或子节点 metadata 能回答的问题，不要靠截图猜。
- 不要把 Figma screenshot 当作本应由 DOM/CSS/组件实现的 UI 素材。
- 不要用占位图或相似 icon 替代 Figma MCP 返回的真实资产。
- 不要给业务后台、表格、筛选和数据管理页面加入厚重营销装饰。
- 不要把固定功能渐变当作品牌渐变；它只用于规范里描述的指标/状态场景。
