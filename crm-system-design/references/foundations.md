# 基础设计规范

本文件是“集团客户 → 我的客户”模块所有视觉参数的唯一规则源。其他文档只能引用这里的 Token，不得复制或重新定义数值。

## 产品基调

- 高密度桌面端企业后台：深色侧栏、白色顶栏、浅灰工作区、白色内容面。
- 采用 Ant Design v4 的视觉语义，不新增主题配置。
- 使用系统默认字体，只输出简体中文；不设计移动端、平板端或国际化布局。
- 常规内容表面扁平、弱阴影、低圆角，不使用营销式大卡片或装饰性大留白。

## 标准 Logo

唯一标准资产为 [standard-logo.svg](../assets/standard-logo.svg)，其中内嵌用户提供的原始 PNG。

- 展开侧栏按原始 208×62 px 显示，保持 104:31 比例和源图内部留白。
- 禁止重绘、替换字体、改字、改色、拉伸、增加蒙层或叠加元素。
- 折叠侧栏只允许随侧栏宽度自然隐藏右侧文字，不得制作近似图标。
- 单文件 HTML 必须从该资产提取同一图像数据并以内联 data URI 使用，不依赖外部路径。

## 布局与尺寸 Token

| Token | 固定值 | 用途 |
|---|---:|---|
| `sider-expanded` | 208 px | 展开侧栏宽度 |
| `sider-collapsed` | 48 px | 折叠侧栏宽度 |
| `header-height` | 48 px | 固定顶栏 |
| `breadcrumb-height` | 48 px | 独立面包屑区域，文字垂直居中 |
| `page-margin` | 10 px | 所有支持宽度的工作区外边距 |
| `module-gap` | 10 px | 任意相邻白色一级模块的垂直间距 |
| `module-padding` | 20 px | 普通白色模块四边内边距 |
| `tabs-module-padding` | 0 20px 20px | 页面级 Tabs 模块；顶部无额外内边距 |
| `control-height` | 32 px | Button、Input、Select、DatePicker |
| `table-toolbar-control-height` | 28 px | 仅表格工具栏小按钮 |
| `button-gap` | 8 px | 同一操作组 |
| `filter-gap` | 16 px | 相邻筛选项 |
| `select-arrow-right` | 12 px | Select 箭头右缘到控件右边框 |
| `table-header-height` | 48 px | 表头；不吸顶 |
| `table-row-height` | 48 px | 单行数据行 |
| `tabs-height` | 48 px | 线型 Tabs 栏及 Tab 点击区 |
| `tabs-gutter` | 32 px | 相邻 Tab 净间距，不作用于首尾 |
| `tabs-ink-height` | 2 px | 激活指示线，贴合底部分隔线 |
| `drawer-view-width` | 480 px | 快速查看 Drawer |
| `drawer-edit-width` | 640 px | 新增和快速编辑 Drawer |
| `delete-modal-width` | 416 px | 删除二次确认弹窗 |

侧栏和顶栏固定吸顶，内容区独立滚动，表格表头不吸顶。页面级 Tabs 必须直接贴合业务模块顶部；Tab 文本在固定高度内垂直居中，内容区与 Tabs 之间再建立正常内容间距。

Select 必须为文字预留右内边距。原生 HTML 隐藏浏览器默认箭头并绘制统一箭头，确保箭头位置不随平台变化。

## 颜色 Token

公司视角操作栏使用 `company-action-height: 48px`，独立于查询行；查询行采用两个等分的弹性字段列和一个自适应宽度的操作组，字段间距引用 `filter-gap`，控件高度引用 `control-height`。

图谱布局 Token：`graph-height: 560px`、`graph-root-width: 240px`、`graph-hq-width: 400px`、`graph-branch-width: 360px`、`graph-column-gap: 64px`。连接线使用 `border` 色，节点圆角 2 px；客户根节点主蓝底白字，总公司使用蓝色图标、标签和边线，分公司使用绿色标签及边线，均沿用公司类型 Token。名称完整换行、常规字重；内容超出图谱区域时内部滚动，不压缩节点至文字不可读。

| Token | 固定值 | 用途 |
|---|---:|---|
| `primary` | `#1C6CEF` | 主按钮、链接、导航选中、进行中、Tabs |
| `sider` | `#2C2E40` | 左侧导航背景 |
| `surface` | `#FFFFFF` | 顶栏和内容面 |
| `page` | `#F5F6F8` | 工作区及下钻返回区 |
| `text-primary` | `#262626` | 标题和主要内容 |
| `text-secondary` | `#8C8C8C` | 元数据和辅助文字 |
| `border` | `#E5E7EB` | 控件、分隔线和弱边框 |
| `success` | `#52C41A` | 成功、完成、启用 |
| `warning` | `#FAAD14` | 待处理、待执行 |
| `danger` | `#FF4D4F` | 失败、关闭、危险操作 |

状态不得只靠颜色表达，必须同时显示文字。类型标签不得借用错误色，除非产品明确把该颜色定义为分类标识。

### 公司类型标签

总公司采用蓝色标签，分公司采用绿色标签，以用户最新提供的标签截图为准；均使用浅色背景、细边框和完整类型文字，不加状态圆点。列表、分公司及关联列表、详情摘要统一使用同一映射。这里的绿色表示分公司类型，不能据此推断业务已开通或成功。

| Token | 固定值 | 用途 |
|---|---|---|
| `company-hq-text` | 引用 `primary` | 总公司标签文字 |
| `company-hq-border` | `#91CAFF` | 总公司标签边框 |
| `company-hq-bg` | `#EAF4FF` | 总公司标签背景 |
| `company-branch-text` | `#52C41A` | 分公司标签文字 |
| `company-branch-border` | `#B7EB8F` | 分公司标签边框 |
| `company-branch-bg` | `#F6FFED` | 分公司标签背景 |

## 排版 Token

分页器采用截图中的轻量样式：整组右对齐，控件高度引用 `control-height`，组内间距引用 `button-gap`；上一页、下一页使用无边框线性箭头，禁用为浅灰色；当前页白底、主蓝色文字与细边框，其他页码无可见边框。底部区域最小高度 64 px，每页条数选择框最小宽度 94 px，箭头位置沿用 `select-arrow-right`。

- 字体栈：`-apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Microsoft YaHei", sans-serif`。
- 正文、表格、控件：14 px / 22 px。
- 总公司汇总、全部公司明细、分公司及关联分公司列表中的公司名称采用常规字重 400，不加粗；表头仍沿用标题字重。
- 行内统计（例如“分公司 N · 联营开票 N”）的文字、数字与单位统一使用正文 14 px / 22 px，按文字基线对齐；仅数字使用字重 600，不放大数字。统计项之间使用间隔点“·”。
- 次要元数据：13 px。
- 模块标题：16 px / 24 px，中等或半粗。
- 实体或页面标题：20–24 px / 28–32 px，中等或半粗。
- 标签：12–14 px。
- 单页最多使用 3 种字重；编号、日期和数量在需要列对齐时使用等宽数字。
- 长内容不得通过缩小到 12 px 以下解决。

## 间距与圆角

基础节奏使用 4、8、12、16、20、24、32 px；只有上表明确的页面级 Token 使用 10 px。

- 4 px：紧凑控件内部图标与文字。
- 8 px：按钮、标签和紧密元数据。
- 12 px：紧凑行或项目。
- 16 px：筛选和常规表单。
- 20 px：普通白色模块。
- 24 px：强内容分组。
- 32 px：谨慎使用的强分隔或 Tabs 相邻项间距。

圆角只允许 0、2、4 px：

- 白色内容区、页面模块、表格容器：0 px。
- 按钮、输入框、选择器：2 px。
- 弹窗及重要浮层面板：4 px。
- 不使用 6、8 px 或胶囊式大圆角，既有状态标签除外。

## 图标

- 产品 Logo 不属于图标系统，必须使用标准资产。
- 通用图标使用 Ant Design Icons v4 可用图标，默认 16 px；顶栏工具图标统一为 16 px。
- 顶栏右侧三个工具图标从左到右固定使用 [top-notice.svg](../assets/top-notice.svg)、[top-todo.svg](../assets/top-todo.svg)、[top-message.svg](../assets/top-message.svg)，分别对应声音通知、待办和消息；必须复用原始资产，不得以字符或其他近似图标替代。待办和消息的数量徽标叠加在各自按钮右上方。
- 同一层级保持统一描边风格。含义不明确的图标必须配文字或 Tooltip。
- 复制操作必须使用 Skill 标准资产 [copy-icon.svg](../assets/copy-icon.svg)，不得使用文本字符、其他复制图标或重新描摹；图标保持原始 16 × 16 px、`#206DEF`，并提供成功反馈。
- 图标按钮必须有可读名称和可见键盘焦点。

## 桌面分辨率

- 最低支持宽度 1280 px；必须覆盖 1280、1366、1440、1920 px。
- 验证视口：1280×720、1366×768、1440×900、1920×1080，并检查浏览器 100% 和 125% 缩放。
- 1280–1439 px 可将次要筛选收进“更多筛选”，表格可横向滚动，但主操作和关键行操作必须可见。
- 低于 1280 px 不在支持范围内；不得为此改变既定桌面布局。
- 不生成移动端导航、移动端断点或用卡片替代表格。
