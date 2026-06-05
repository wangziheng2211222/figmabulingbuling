# 蝉圈圈设计速查表

用途：高频还原与评审时快速查值。完整说明、完整色阶和组件细节见 `chanquanquan-design.md`。

## 1. 核心气质

- 风格：轻量业务系统、增长分析产品、清晰运营工作台。
- 页面：浅灰框架背景 + 白色内容面 + 低对比边框。
- 强调：品牌珊瑚橙只用于主操作、选中态、品牌强调和关键行动。
- 避免：厚重营销装饰、大面积重色渐变、随意透明黑、临时发明品牌色。

## 2. 高频颜色

| 用途 | 色值 | Token |
|---|---|---|
| 品牌主色 / 主按钮 / 主交互 | `#FF7752` | `color-primary-default` |
| 品牌 Hover | `#FF9275` | `color-primary-light-20` |
| 品牌 Click / Active | `#E56B4A` | `color-primary-dark-10` |
| 品牌禁用底色 | `#FFD6CB` | `color-primary-light-70` |
| 品牌加载 / 弱禁用 | `#FFC9BA` | `color-primary-light-60` |
| 品牌浅背景 | `#FFF8F6` | `color-primary-light-95` |
| 品牌浅背景 2 | `#FFF1EE` | `color-primary-light-90` |
| 页面框架背景 | `#F7F8FA` | `color-gray-default-01` |
| 弱分割 / Tag 底 | `#F2F3F5` | `color-gray-default-02` |
| 默认边框 / 表单边框 | `#E5E6EC` | `color-gray-default-03` |
| 一级文字 / 标题 | `#1D2129` | `color-gray-default-primary` |
| 正文 / 副标题 | `#4E5969` | `color-gray-default-08` |
| 辅助信息 / 表头 | `#86909C` | `color-gray-default-06` |
| 禁用文字 | `#A9AEB8` | `color-gray-default-05` |
| 白色内容面 | `#FFFFFF` | `color-basic-white-default` |

## 3. 功能色

| 语义 | 主色 | 浅背景 | 深色文字 | 用法 |
|---|---|---|---|---|
| 信息 / 图表蓝 | `#5771FF` | `#F2F4FF` | `#344499` | 图表、蓝色数据卡 |
| 成功 / 下降改善 | `#00B489` | `#EBF9F6` | `#006C52` | 成功、正向改善 |
| 警示 | `#FF9A1D` | `#FFF8E8` | `#A65508` | 警示、提醒 |
| 错误 / 危险 / 上升风险 | `#F54B45` | `#FFEDE8` | `#A1171B` | 错误、失败、危险 |
| 紫色辅助 | `#722ED1` | `#F5E8FF` | `#3C108F` | 图表辅助、强调 |
| 蔚蓝辅助 | `#027FFF` | `#EBF5FF` | `#014C99` | 图表辅助、信息强调 |

## 4. 字体层级

默认字体：PingFang SC。

| 层级 | 字号 | 字重 | 行高 | 用法 |
|---|---:|---|---:|---|
| 页面一级标题 | 24pt | Medium / Regular | 36pt | 系统级页面标题 |
| 二级标题 | 20pt | Medium / Regular | 30pt | 页面分区标题 |
| 大卡片标题 | 18pt | Medium / Regular | 26pt | 重要卡片标题 |
| 卡片/模块标题 | 16pt | Medium / Regular | 24pt | 常规模块标题 |
| 正文 | 14pt | Regular | 22pt | 默认正文、表格正文 |
| 辅助文字 | 12pt | Regular | 18pt | 注释、时间戳、说明 |
| 极小标签 | 10pt | Regular | 12pt | 低频极小标签 |

文字颜色：标题 `#1D2129`，正文 `#4E5969`，辅助 `#86909C`，禁用 `#A9AEB8`，反色 `#FFFFFF`。

## 5. 按钮

| 尺寸 | 高度 | 文字 | 行高 | 横向 Padding | icon | icon/text |
|---|---:|---:|---:|---:|---:|---:|
| 超大 | 40px | 16px | 24px | 20px | 16px | 6px |
| 大 | 36px | 14px | 22px | 14px | 16px | 6px |
| 默认 | 32px | 14px | 22px | 14px | 16px | 6px |
| 小 | 28px | 14px | 22px | 14px | 16px | 6px |
| 迷你 | 24px | 12px / 14px | 16px / 22px | 14px | 16px | 6px |

- 默认圆角：矩形按钮和图标按钮 `6px`。
- Primary：背景 `#FF7752`，文字 `#FFFFFF`。
- Secondary：背景 `#FFFFFF`，文字 `#1D2129` / `#4E5969`，边框 `#E5E6EC`。
- Text Button：透明背景，品牌文字 `#FF7752`。
- Disabled：品牌禁用底 `#FFD6CB`，禁用文字可用 `#A9AEB8`。

## 6. 常用组件

| 组件 | 默认规则 |
|---|---|
| 页面背景 | `#F7F8FA` |
| 默认卡片 | `#FFFFFF` 背景，`#E5E6EC` 或 `#F2F3F5` 边框 |
| 品牌选中卡片 | `#FFF8F6` / `#FFF1EE` 背景，强调 `#FF7752` |
| 表格 | 表头 `#F7F8FA`，线 `#F2F3F5` / `#E5E6EC`，表头字 `#86909C` |
| 表单 | 边框 `#E5E6EC`，聚焦用品牌色，错误用 `#F54B45` |
| 默认 Tag | `#F2F3F5` 背景，`#4E5969` 文字 |
| 品牌 Tag | `#FFF8F6` 背景，`#FF7752` 文字 |
| 分割线 | `#F2F3F5` / 1px，需要更明确边界时用 `#E5E6EC` |

## 7. 标题栏

- 通用标题栏高度：`76px`。
- Tabs 标题栏高度：`64px`。
- 左右 Padding：`24px`。
- 上下 Padding：`16px`。
- 底部分割线：`#F2F3F5`。
- 标题：17px / Semibold / 24px / `#1D2129`。
- 副标题：12px / Regular / 16px / `#86909C`。
- 标题与说明 icon 间距：`4px`。
- 副标题文案与说明 icon 间距：`6px`。
- 右侧按钮组合间距：`12px`。

## 8. 渐变

| 用途 | Token | 色值 |
|---|---|---|
| 品牌重色渐变 | `color-gradient-primary-01` | `linear-gradient(45deg, #FFC9BA 0%, #FF7752 100%)` |
| 品牌浅色渐变 | `color-gradient-primary-02` | `linear-gradient(-45deg, #FFF8F6 0%, #FFF1EE 100%)` |
| 红色指标渐变 | `color-gradient-red-01` | `linear-gradient(90deg, #F68052 0%, #FF9A64 43%, #FFBE8E 100%)` |
| 紫色指标渐变 | `color-gradient-purple-01` | `linear-gradient(90deg, #4C67FF 0%, #ACB5FF 100%)` |
| 黄色指标渐变 | `color-gradient-yellow-01` | `linear-gradient(90deg, #FE7400 0%, #FFCA42 100%)` |
| 蓝色指标渐变 | `color-gradient-blue-01` | `linear-gradient(90deg, #027FFF 0%, #7ABBFF 100%)` |
| 绿色指标渐变 | `color-gradient-green-01` | `linear-gradient(90deg, #0EAC8E 0%, #3DE7A0 100%)` |
| 灰色未选中渐变 | `color-gradient-grey-01` | `linear-gradient(90deg, #F7F8FA 0%, #F2F3F5 59%, #E5E6EC 100%)` |

品牌相关、可换肤、菜单 icon 用品牌渐变；指标卡重色状态用固定功能渐变，不参与品牌换肤。

## 9. Token 取值顺序

1. 具体设计稿或组件实例上已定义的变量、样式或组件属性。
2. 当前组件库规范中的 Token。
3. 同类组件的语义规则，例如按钮、卡片、Tag、表格。
4. 相邻色阶或视觉近似值，并标注为推导值。

## 10. 易错提醒

- 不要把品牌主色过度用于多序列图表。
- 不要把固定功能渐变当作品牌渐变。
- 不要用临时蓝色焦点环替代品牌聚焦态。
- 不要直接使用纯黑 `#000000` 做系统正文。
- 不要给表格、筛选、后台页面加入厚重营销装饰。
- 不要在已有相近 Token 时发明新颜色。
