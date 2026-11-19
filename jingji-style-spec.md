# 静记 · 全局组件样式参数说明

> 对应原型：`jingji-prototype.html`
> 设计规范：Material 3 Baseline（Flutter `useMaterial3: true` 默认样式）
> 画布：固定 375 × 812 px，所有尺寸为固定像素，无响应式、无缩放
> 原则：只使用 M3 默认颜色角色与默认组件尺寸，不新增自定义色值、圆角、阴影

---

## 1. 画布与页面骨架

| 项目 | 参数 |
|---|---|
| 画布尺寸 | 375 × 812 px |
| 状态栏（占位） | 28 px |
| 顶部 AppBar | 64 px |
| 页面内容区内边距 | 16 px（列表页横向 16，列表行左右 16） |
| 页面纵向间距 | 16 px（笔记列表 12 px） |
| 底部 NavigationBar | 80 px |
| FAB 右边距 / 底边距 | 16 px / 96 px（= 导航栏 80 + 16） |

页面纵向结构：`状态栏 → AppBar → 内容区（可滚动）→ [FAB] → NavigationBar`

---

## 2. 颜色令牌（Light，M3 Baseline）

| 角色 | 色值 | 用途 |
|---|---|---|
| primary | `#6750A4` | 主按钮、选中态、分组标题、单选/复选 |
| onPrimary | `#FFFFFF` | 主按钮文字、开关手柄 |
| primaryContainer | `#EADDFF` | LOGO 底、FAB 背景 |
| onPrimaryContainer | `#21005D` | FAB 图标、LOGO 图标 |
| secondaryContainer | `#E8DEF8` | 选中 Chip、导航选中指示器、序号圆点 |
| onSecondaryContainer | `#1D192B` | 选中 Chip / 导航文字 |
| errorContainer | `#F9DEDC` | 风险提示卡背景 |
| onErrorContainer | `#410E0B` | 风险提示文字 |
| surface / background | `#FFFBFE` | 页面背景 |
| onSurface | `#1C1B1F` | 主文字、图标 |
| surfaceVariant | `#E7E0EC` | 搜索框等容器 |
| onSurfaceVariant | `#49454F` | 次级文字、未选中图标 |
| outline | `#79747E` | 输入框 / Chip 边框、开关未选中 |
| outlineVariant | `#CAC4D0` | 1 px 分隔线、卡片描边 |
| surfaceContainerLowest | `#FFFFFF` | 高亮卡片 |
| surfaceContainerLow | `#F7F2FA` | 笔记卡片 |
| surfaceContainer | `#F3EDF7` | 底部导航栏 |
| surfaceContainerHigh | `#ECE6F0` | 搜索框、提示卡 |
| surfaceContainerHighest | `#E6E0E9` | 填充卡片、缩略图底、开关轨道 |

深色预览仅用于主题页（M3 默认深色）：
`surface #1C1B1F`、`surfaceContainer #211F26`、`onSurface #E6E0E9`、
`primary #D0BCFF`、`secondaryContainer #4A4458`、`primaryContainer #4F378B`。

Flutter 落地：`ThemeData(useMaterial3: true)` 不指定 seedColor，即得到上述 Baseline 配色；深色使用对应 `ColorScheme.dark()`。

---

## 3. 字体层级（M3 Typescale，Roboto / 系统中文回退）

| 样式 | 字号 / 行高 | 字重 | 用途 |
|---|---|---|---|
| headlineSmall | 24 / 32 | 400 | 解锁页 App 名、备份时间 |
| titleLarge | 22 / 28 | 400 | AppBar 标题（首页 22） |
| titleMedium | 16 / 24 | 500 | 笔记标题、列表标题、卡片标题 |
| titleSmall | 14 / 20 | 500 | 字段小标题（标签、附件、备份记录） |
| bodyLarge | 16 / 24 | 400 | 待办正文、输入框文字 |
| bodyMedium | 14 / 20 | 400 | 正文、笔记摘要、说明文字 |
| bodySmall | 12 / 16 | 400 | 辅助说明、时间、文件大小 |
| labelLarge | 14 / 20 | 500 | 按钮文字、Chip 文字、分组标题 |
| labelMedium | 12 / 16 | 500 | 导航栏标签 |

---

## 4. 组件参数

### 4.1 顶部 AppBar（Small Top AppBar）
- 高度：64
- 标题：titleLarge 22 / 28，左内边距 12（图标按钮之后）
- 图标按钮：48 × 48 点击区域，圆形，图标 24
- 颜色：surface 背景，onSurface 标题，onSurfaceVariant 图标
- 无分割线（M3 默认）

### 4.2 底部导航（NavigationBar）
- 高度：80，背景 surfaceContainer（`#F3EDF7`）
- 项数：3（笔记 / 待办 / 设置）
- 选中指示器：64 × 32，圆角 16，secondaryContainer
- 图标：24；选中图标颜色 onSecondaryContainer
- 标签：labelMedium 12 / 16，500；图标与文字间距 4

### 4.3 FAB
- 尺寸：56 × 56，圆角 16
- 背景：primaryContainer；图标：onPrimaryContainer，24
- 位置：右 16、底 96（在导航栏上方 16）
- 阴影：M3 elevation 1

### 4.4 按钮
| 类型 | 高度 | 圆角 | 左内边距 | 文字 | 背景 / 文字色 |
|---|---|---|---|---|---|
| Filled | 40 | 20 | 24 | labelLarge 14/20 500 | primary / onPrimary |
| Outlined | 40 | 20 | 24 | labelLarge | 透明 + 1 px outline / primary |
| Text | 40 | 20 | 12 | labelLarge | 透明 / primary |
| Disabled | 40 | 20 | — | labelLarge | onSurface 12% / onSurface 38% |

按钮内图标 18，图标与文字间距 8。整行按钮 `width: 100%`。

### 4.5 输入框（Outlined TextField）
- 高度：56；圆角：4；边框：1 px outline
- 文字：16 / 24；左右内边距 16
- 浮动标签：12 / 16，位于上边框（top -8），左右留 4 px 背景遮挡
- 尾部图标按钮：48 × 48，圆形
- 多行正文：最小高度 200，内边距 16，行高 24
- 聚焦态按 M3 默认（primary 边框 2 px），原型未额外绘制

### 4.6 搜索栏（SearchBar）
- 高度 56，圆角 28，背景 surfaceContainerHigh
- 左右内边距 16，左侧搜索图标 24，图标与文字间距 16
- 文字：16 / 24，颜色 onSurfaceVariant（占位）

### 4.7 Chip（FilterChip / AssistChip）
- 高度 32，圆角 8，左右内边距 12
- 文字：14 / 20，500
- 未选中：透明底 + 1 px outline，文字 onSurfaceVariant
- 选中：secondaryContainer 底，无边框，文字 onSecondaryContainer，前置勾选图标 18
- 图标与文字间距 8
- AssistChip 使用 outlineVariant 边框，前置 18 图标

### 4.8 卡片（Card）
- 圆角 12，内边距 16，子项间距 8
- Elevated（笔记卡）：surfaceContainerLow + elevation 1
- Filled（备份状态、同步规则）：surfaceContainerHighest，无阴影
- Outlined（附件、存储说明、备份记录）：surface + 1 px outlineVariant
- 可点击卡片悬停时 elevation 2

### 4.9 列表项（ListItem）
- 单行最小高度 56；双行最小高度 72
- 左右内边距 16，左图标与文字间距 16
- 标题 16 / 24；副标题 12 / 16，onSurfaceVariant
- 尾部箭头图标 24，onSurfaceVariant
- 行间分隔线：1 px outlineVariant，与内容左对齐以外通栏
- 点击行可按 M3 使用 4% onSurface 状态层

### 4.10 开关（Switch）
- 轨道 52 × 32，圆角 16，边框 2
- 关闭：轨道 surfaceContainerHighest，边框 outline，手柄 16×16 outline
- 打开：轨道 primary，手柄 24×24 onPrimary，右对齐
- 触控区域 ≥ 48

### 4.11 复选框（Checkbox）
- 尺寸 18 × 18，圆角 2，边框 2 px onSurfaceVariant
- 选中：primary 填充 + 白色勾，勾线宽 2

### 4.12 单选框（Radio）
- 尺寸 20 × 20，圆环 2 px
- 选中：圆环 primary，内部实心圆 primary（内缩 3）
- 行高 56，左右内边距 16，图标与文字间距 16

### 4.13 分割线
- 统一 1 px，颜色 outlineVariant
- 列表行分割线通栏；卡片内分割线由左右内边距内缩

### 4.14 提示 / 风险卡
- 信息提示：surfaceContainerHigh 背景，圆角 12，内边距 16
  - 图标 20，primary；文字 12 / 16，onSurfaceVariant
- 风险提示：errorContainer 背景，文字 onErrorContainer，布局同上
- 图标与文字间距 12

### 4.15 其他
- 缩略图：40 × 40，圆角 8，surfaceContainerHighest 底
- 内容区滚动条：原生滚动，不自定义
- 图标：Material Icons，24 / 18 / 16 三档，颜色继承文字角色
- 状态栏：原型固定 28 px 占位（真机由系统控制）

---

## 5. 页面级组合

| 页面 | 主体布局 | 关键组件 |
|---|---|---|
| 01 解锁 | 垂直居中，间距 24 | TextField（密码）、FilledButton、TextButton ×2、InfoCard |
| 02 笔记列表 | 纵向 12，滚动 | SearchBar、FilterChip 行、Card ×3、FAB、NavigationBar |
| 03 笔记编辑 | 纵向 16，滚动 | TextField ×2、InputChip 行、OutlinedCard（附件）、AssistChip 行、InfoCard |
| 04 标签管理 | 列表，无底部导航 | ListItem 双行 ×4、OutlinedButton 通栏 |
| 05 待办 | 纵向 12 | FilterChip、Card + Checkbox ×3、FAB、NavigationBar |
| 06 设置 | 分组列表 | 分组标题 primary + ListItem 双行 ×8、NavigationBar |
| 07 隐私与存储 | 纵向 16 | 图标 + 标题、OutlinedCard 三行、ErrorCard、OutlinedButton |
| 08 加密与生物识别 | 分组列表 | ListItem + Switch ×3、ListItem + chevron、InfoCard |
| 09 主题 | 单选列表 + 预览 | Radio 行 ×3、浅/深色预览卡、InfoCard |
| 10 备份与恢复 | 纵向 16 | FilledCard 状态、Filled/Outlined 按钮、Switch 行、备份记录卡、InfoCard |
| 11 云同步 | 纵向 16 | Switch 行、FilledCard 步骤 ×3、禁用 FilledButton、InfoCard |

---

## 6. HTML → Flutter 组件对应

| HTML | Flutter（Material 3 默认） |
|---|---|
| `.phone` | `Scaffold`（固定 375 宽预览容器） |
| `.appbar` | `AppBar(toolbarHeight: 64)` |
| `.navbar` | `NavigationBar(height: 80, destinations: ...)` |
| `.fab` | `FloatingActionButton`（默认 56 / 圆角 16） |
| `.btn.filled` | `FilledButton` |
| `.btn.outlined` | `OutlinedButton` |
| `.btn.text` | `TextButton` |
| `.field`（outlined） | `TextField` + `OutlineInputBorder(borderRadius: 4)` |
| `.searchbar` | `SearchBar`（默认高 56 / 圆角 28） |
| `.chip` | `FilterChip` / `ActionChip` / `AssistChip` |
| `.card` | `Card`（默认圆角 12） |
| `.list-row` | `ListTile` / `SwitchListTile` / `CheckboxListTile` / `RadioListTile` |
| `.checkbox` | `Checkbox` |
| `.radio` | `Radio` |
| `.switch` | `Switch` |
| `.divider` | `Divider(height: 1, thickness: 1)` |
| `.body` | `ListView` / `SingleChildScrollView` + `Padding(16)` |
| 图标 | `Icons.xxx`（Material Icons） |

---

## 7. 交互范围（原型已实现）

- 页面跳转：解锁 → 笔记列表；笔记卡片 / FAB → 编辑页；标签 Chip → 标签管理；底部导航三页互跳；设置 → 各二级页；隐私页 → 备份页
- Chip 同组互斥选中；Switch 点击切换；Checkbox 点击勾选；主题单选切换；收藏星标切换
- 不含：真实增删改查、搜索过滤、排序弹窗、备份执行、网络请求、状态持久化

## 8. 转换到 Flutter 时的注意事项

1. 只使用 `ThemeData(useMaterial3: true)` 默认主题，不写 `Color(...)` 自定义颜色。
2. 尺寸用常量（`AppBar` 用默认 64 以外的工具栏高度时才显式设置），避免在组件里写死 375。
3. 页面内边距统一 `EdgeInsets.all(16)`，纵向间距用 `SizedBox(height: 16)` 或 `ListView.separated`。
4. 输入框使用 `OutlineInputBorder`，圆角 4，标签用 `floatingLabelBehavior: FloatingLabelBehavior.always`。
5. 列表使用 `ListTile` 的默认 `minVerticalPadding` 与 `contentPadding: EdgeInsets.symmetric(horizontal: 16)`。
6. 卡片使用 `Card` 默认圆角 12，不额外加 `shape`。
7. 主题切换只改 `ThemeMode`，深色配色交给 `ColorScheme.dark()`。
