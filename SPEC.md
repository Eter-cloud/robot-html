# SPEC.md - 具身智能狂热之下：一场不知道终点的马拉松

## 1. Concept & Vision

这是一篇数据新闻专题，以童话绘本的叙事方式讲述具身智能（人形机器人）行业的狂热与隐忧。整体氛围如同翻阅一本精装绘本——线条柔和、色彩梦幻、手绘质感强烈，却承载着严肃的产业观察。读者将在诗意与数据之间，感受这场"终点未知的马拉松"。

## 2. Design Language

### 美学方向
童话绘本风格：如同 Nils Hildstrom 和 Bea 等插画师的柔和叙事风格，线条简洁流畅，色彩梦幻柔和，带有手绘质感的纹理感。

### 调色板
- **Primary**: `#5B7DB1` (梦幻蓝)
- **Secondary**: `#E8B4B8` (玫瑰粉)
- **Accent**: `#A8D5BA` (薄荷绿)
- **Accent2**: `#F4E1A8` (暖金色)
- **Background**: `#FDF8F3` (奶油白)
- **Text**: `#3D3D3D` (深灰)
- **Text-light**: `#7A7A7A` (浅灰)
- **Chapter colors**: 每章节独特的柔和色调

### 字体
- 标题: `'Noto Serif SC', Georgia, serif` - 衬线体营造故事感
- 正文: `'Noto Sans SC', -apple-system, sans-serif`
- 数据强调: `'ZCOOL XiaoWei', serif` - 手写质感

### 空间系统
- 基础单位: 8px
- 章节间距: 120px (大留白如绘本的页边距)
- 内容最大宽度: 900px
- 行高: 1.8 (阅读舒适如翻书)

### 动效哲学
- 滚动触发的淡入效果 (opacity 0→1, 600ms ease-out)
- 元素交错进入 (stagger 100ms)
- 悬停时轻微上浮 (translateY -4px)
- 页面切换如翻书的视差效果
- 数据展开时柔和的 accordion 效果

### 视觉资产
- 手绘风 SVG 插画 (机器人、跑道、云朵等)
- 数据使用 <span> 标签包裹，带有高亮背景
- 图标使用线性 SVG，带有手绘质感
- 装饰元素: 圆点、波浪线、小星星

## 3. Layout & Structure

### 页面结构
```
[封面] - 全屏沉浸式，图片
[第一章] - 人形机器人马拉松开篇 (横向叙事流动)
[第二章] - 投资热潮 (卡片瀑布流 + 数据高亮)
[第三章] - 展会营销揭秘 (时间线叙事)
[第四章] - 技术瓶颈 (图解可视化)
[第五章] - 从业者群像 (人物卡片 + 引用)
[第六章] - 审慎乐观收尾 (开放式结尾)
[Footer] - 留白 + 作者信息
```

### 响应式策略
- Desktop (>1024px): 全特效，横向装饰元素
- Tablet (640-1024px): 简化装饰，保持核心布局
- Mobile (<640px): 单列布局，触摸友好的交互

## 4. Features & Interactions

### 核心交互
- **数据高亮**: `<span class="data-highlight">` 包裹关键数字，点击展开详情卡片
- **金句交互**: `<span class="quote-trigger">` 点击显示完整引用
- **锚点导航**: 右侧迷你导航栏，点击平滑跳转
- **章节进度**: 滚动时顶部显示当前章节指示器

### 展开详情
- 点击数据 → 展开详情卡片 (slide-down + fade)
- 再次点击或点击外部 → 收起
- ESC 键也可收起

### 滚动动画
- 元素进入视口 20% 时触发动画
- 动画只触发一次
- 和弦效果: 多个元素依次进入

## 5. Component Inventory

### DataHighlight (数据高亮)
- Default: 带背景色的数字/文字
- Hover: 轻微放大 + 下划线提示可点击
- Active/Expanded: 下方展开详情卡片
- 背景色: `rgba(91, 125, 177, 0.15)`

### QuoteTrigger (金句触发器)
- Default: 带引号装饰的关键词
- Hover: 颜色变化 + 呼吸动画
- Active: 显示完整引用浮层

### ChapterNav (章节导航)
- 右侧迷你垂直导航
- 当前章节高亮
- 点击跳转 + 平滑滚动

### ChapterCard (章节卡片)
- 大标题 + 章节编号
- 装饰性边线
- 淡入动画

### PersonCard (人物卡片)
- 头像区 (手绘风格)
- 引用文字
- 职业/身份标签

### TechDiagram (技术图解)
- SVG 流程图
- 手绘风格线条
- 动画展示瓶颈点

## 6. Technical Approach

### 技术栈
- 纯 HTML5 + CSS3 + Vanilla JavaScript
- 单文件实现
- 无外部依赖 (除 Google Fonts)

### CSS 特性
- CSS Custom Properties (变量)
- CSS Grid + Flexbox
- CSS Animations + Transitions
- Scroll Snap (可选，翻书效果)
- `IntersectionObserver` API

### 性能优化
- CSS 动画使用 `transform` 和 `opacity`
- 减少重排重绘

### 移动端适配
- 触摸事件支持
- 视口单位 (vw, vh, dvh)
- 媒体查询断点
