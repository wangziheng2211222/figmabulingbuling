# Design Restoration Reference Index

Use this index during design restoration to decide which sections of `chanquanquan-design.md` to load after reading the exact Figma node. The Figma node remains the source of truth; this reference fills in component-library semantics, token choices, and missing style guidance.

| Need | Load sections | Search terms |
|---|---|---|
| Overall product visual style | `1`, `7` | `Visual Theme`, `Design System Notes` |
| Buttons, primary action, selected state, links | `2.1`, `2.2`, `4.1`, `6.2` | `品牌主色`, `Primary`, `按钮`, `Button`, `尺寸`, `图标按钮`, `#FF7752` |
| Page background, borders, text hierarchy | `2.1`, `2.3`, `3`, `5`, `6.4` | `中性灰阶`, `Typography`, `Layout`, `#F7F8FA` |
| Cards and content surfaces | `4.2`, `5` | `卡片 Card`, `页面结构` |
| Title bars, page headers, modal/drawer headers | `3`, `4.10`, `5`, `6.4` | `标题栏`, `Title Bar`, `弹窗`, `抽屉`, `Tabs`, `副标题`, `关闭 icon` |
| Dividers and content separation | `2.3`, `4.11`, `5`, `6.2` | `分割线`, `Divider`, `直线`, `虚线`, `垂直分割线`, `文字+直线`, `纯文字`, `#F2F3F5` |
| Metric cards and charts | `2.4`, `2.5`, `4.3`, `4.8`, `6.3` | `数据卡`, `指标卡`, `图表`, `渐变` |
| Navigation and menu | `2.5`, `4.4`, `6.3` | `导航`, `菜单`, `icon`, `品牌重色渐变` |
| Tables and dense business lists | `4.5`, `5` | `表格 Table`, `Tag 底色`, `扫描效率` |
| Forms, focus, validation | `4.6`, `6.2` | `表单 Form`, `Placeholder`, `聚焦态`, `错误态` |
| Tags, badges, statuses | `2.4`, `4.7`, `6.2` | `标签`, `Badge`, `Tag`, `成功`, `失败`, `警示`, `信息` |
| Marketing banners | `3`, `4.9`, `7` | `宣发`, `Banner`, `56pt`, `48pt`, `36pt` |
| Token precedence and fallbacks | `6.1`, `8` | `Token 优先级`, `待补充项`, `推导值` |

Default rule: load Figma context and screenshots first, inspect child nodes/assets when needed, then use this index to load the minimum reference sections needed to explain missing styles or validate implementation choices.
