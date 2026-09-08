# Ant Design v4 组件映射

本文件只定义组件选择与组合方式。视觉参数全部读取 [基础设计规范](foundations.md)，页面结构读取 [页面与业务流程](my-customers-pages.md)，不得在此重复 Token。

本产品固定使用 Ant Design v4，不引用 v5 专属 Token、组件或 API，也不新增主题配置。单文件 HTML 可用原生 HTML/CSS/JavaScript实现等价视觉和行为，不需要联网加载 React 或 Ant Design。

| CRM 场景 | Ant Design v4 组件或模式 | 组合规则 |
|---|---|---|
| 应用骨架 | `Layout`、`Sider`、`Header`、`Content` | 固定壳层，内容独立滚动；尺寸使用基础 Token |
| 标准 Logo | 原生 `img` 或内联图像 | 使用 Skill 标准资产，不用图标或文字重绘 |
| 全局导航 | `Menu mode="inline"` | 受控 selected/open keys；折叠项配 Tooltip |
| 面包屑 | `Breadcrumb` | 当前项不可点击，上级项可导航 |
| 下钻返回 | `Button`、`ArrowLeftOutlined` | 独立返回区；恢复来源状态 |
| 标题与摘要 | `Typography.Title`、`Space`、`Tag` | 克制的实体摘要，不做营销式页头 |
| 复制编号 | `Typography.Text copyable` 或图标按钮 | 图形使用基础规范指定的 Skill 标准复制图标资产，并提供可读名称和成功反馈 |
| 顶栏工具 | `Badge`、`Button`、`Dropdown`、`Avatar` | 紧凑单行布局 |
| 内容模块 | `Card` 或语义容器 | 扁平，避免嵌套卡片 |
| 详情 Tabs | `Tabs` | 线型；`tabBarGutter` 绑定基础 Token；状态受控 |
| 筛选与表单 | `Form`、`Input`、`Select`、`DatePicker`、`Cascader`、`TreeSelect` | 按字段关系选择控件；尺寸使用基础 Token |
| 更多筛选 | `Collapse`、`Popover` 或条件表单行 | 显示生效条件并保持可发现 |
| 查询与重置 | 主 `Button`、默认 `Button` | 受控查询，不由输入自动触发 |
| 页面操作 | `Button`、`Dropdown.Button` | 区分页面级和结果级操作 |
| 数据列表 | `Table` | 设置 `rowKey`、分页、loading、scroll、ellipsis 和当前页选择 |
| 状态与类型 | `Tag`、`Badge` | 语义样式集中映射，颜色与文字并用 |
| 分页 | `Pagination` 或 Table pagination | 总数、页码和每页数量受控 |
| 删除确认 | `Modal.confirm` | 明确对象与后果；只用于需要确认的操作 |
| 新增/编辑/查看 | `Drawer` | 内容滚动、底部操作区固定、保留背景上下文 |
| 只读详情 | `Descriptions` 或信息网格 | 不用禁用表单伪装 |
| 反馈 | `message`、`notification`、`Alert`、`Result` | 按反馈范围和持续时间选择 |
| 加载 | `Skeleton`、`Spin`、组件 `loading` | 区分首次加载和局部刷新 |
| 空状态 | `Empty` | 区分首次无数据和筛选无结果 |
| 批量流程 | `Steps`、`Upload.Dragger`、`Progress`、`Table` | 表达上传、检查、执行和结果 |
| 卡片/列表切换 | 按钮样式 `Radio.Group` | 不使用 v5 `Segmented` |
| 公司列表视角切换 | 按钮样式 `Radio.Group` | 三选一受控状态；切换视角不改变客户详情 Tab |
| 公司关系图谱 | 语义按钮节点 + 自定义 SVG/连接线，或适合层级的 `Tree` 组合 | 节点可聚焦、可读、可进入详情；不引入图谱库依赖 |
| 下级公司/门店列表 | `Table`、`Tag`、`Pagination` | 使用视图栈返回实际来源；表格字段服从页面规范 |
| 业务状态禁用 | `Tooltip` + 禁用控件 | 解释业务原因，不扩展权限设计 |
| 桌面栅格 | `Grid`、`Row`、`Col`、`Space` | 仅桌面断点；不使用 v5 `Flex` |

## 组合约束

- `Space` 只用于行内操作组，不作为整页栅格。
- 没有表单语义时，不为对齐滥用 `Form.Item`。
- `Badge` 圆点不能单独承担业务状态。
- 禁用控件的 Tooltip 使用正确包装，保证指针、焦点和可读名称。
- 表格虚拟化只解决大量客户端渲染，不能替代服务端分页。
- 所有页面级样式变量集中映射到基础规范 Token，不在组件文件散落新值。
