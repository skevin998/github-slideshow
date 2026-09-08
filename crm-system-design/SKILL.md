---
name: crm-system-design
description: 基于现有产品截图与 Ant Design v4，设计、扩展或评审“集团客户 → 我的客户”模块的桌面端 UI、交互及业务流程，并统一交付为可直接打开的高保真交互 HTML。适用于客户列表、客户详情五个业务 Tab、公司详情下钻、新增/编辑抽屉和批量设置流程；不适用于其他 CRM 部门模块、移动端或国际化产品。
---

# CRM 系统设计

为“集团客户 → 我的客户”生成或评审高密度桌面端界面。Skill 同时约束 UI、交互与业务流程，以用户确认规则优先，以 Ant Design v4 为组件基准。

## 范围

- 只覆盖“集团客户 → 我的客户”及其直接产生的详情、下钻、Drawer 和批量流程。
- 共享侧栏、顶栏和工作区只作为应用壳层；不得从截图中的其他部门菜单推导业务规则。
- 设计类任务默认交付一个可直接打开的高保真交互 HTML，不生成移动端或多语言版本。

## 单一规则源

| 文件 | 唯一职责 |
|---|---|
| [references/foundations.md](references/foundations.md) | 所有视觉 Token、Logo、布局、颜色、排版、间距、尺寸、圆角和桌面分辨率 |
| [references/patterns.md](references/patterns.md) | 导航、Tabs、筛选、表单、按钮、表格、状态、分页、Drawer、反馈和上下文保留行为 |
| [references/my-customers-pages.md](references/my-customers-pages.md) | 页面层级、字段结构、打开方式、返回目标和业务流程 |
| [references/antd-mapping.md](references/antd-mapping.md) | Ant Design v4 组件选择与组合方式 |
| [references/html-delivery.md](references/html-delivery.md) | 单文件 HTML 的实现边界、交互覆盖和验证流程 |
| [references/screenshot-baseline.md](references/screenshot-baseline.md) | 截图观察及证据边界，不保存已确认 Token |
| [references/source-images.md](references/source-images.md) | 原始截图与标准 Logo 的来源索引 |
| [references/open-questions.md](references/open-questions.md) | 仍未确认且需要按具体需求决定的事项 |
| [references/review-checklist.md](references/review-checklist.md) | 交付检查入口，只引用上述规则，不重复参数 |

具体数值只能在 `foundations.md` 定义。页面文件不得复制全局 Token，交互文件不得复制页面字段，交付和检查文件不得另建一套规则。

## 执行路由

1. 所有任务先读取页面地图，确定层级、打开方式和业务范围。
2. 涉及任何 UI 生成或视觉评审时读取基础规范，并直接复用 [assets/standard-logo.svg](assets/standard-logo.svg)。
3. 涉及交互、状态或操作流程时读取组件与交互模式。
4. 需要指定 Ant Design 实现时读取组件映射。
5. 生成原型或页面时必须读取 HTML 交付规范；仅解释或评审时不强制生成 HTML。
6. 只有需要追溯截图依据时才读取截图基线和来源索引。
7. 只有未决事项会影响本次结果时才读取并提出待确认问题。
8. 交付前执行评审清单。

## 不可变约束

- 使用 Ant Design v4 语义，不引用 v5 专属组件、Token 或视觉特征，也不新增主题配置。
- 保留截图中的高密度桌面端产品语言，默认简体中文，暂不设计权限控制。
- 标准 Logo 必须直接复用 Skill 资产；不得重绘、替换文字、改色、变形或叠加元素。
- 页面与交互必须保持来源上下文，具体打开、返回和状态恢复规则以页面地图和交互模式为准。
- HTML 必须为单文件、断网可用、内联资源、可完成需求范围内的核心流程；不得以静态截图或说明文档代替。
- 一个页面任务只覆盖该页面及验证核心流程必需的关联视图；只有用户明确要求完整模块时才在同一 HTML 中覆盖全部页面。
- 状态必须同时包含文字，业务状态导致的不可用操作应解释原因。
- 规则冲突优先级：用户本次明确要求 → 本 Skill 的单一规则源 → 截图观察 → Ant Design v4 默认规范。重大冲突应说明，不得静默创造例外。
