# GitHub 个人主页设计方案

## 项目概述
为 ZestBox-18 创建现代极简风格的 GitHub 个人主页，包含贪吃蛇动画和热门语言统计卡片。

## 核心功能

### 1. 贪吃蛇动画
- **技术方案**：使用 [Platane/snk](https://github.com/Platane/snk) GitHub Action
- **工作原理**：
  - GitHub Action 每天 UTC 00:00 自动运行
  - 从用户贡献图提取数据
  - 生成贪吃蛇动画 SVG
  - 输出到 `output` 分支
- **引用方式**：在 README.md 中引用 `output` 分支的 SVG 文件

### 2. 热门语言卡
- **技术方案**：使用 [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) API
- **API 端点**：`https://github-readme-stats.vercel.app/api/top-langs/`
- **参数配置**：
  - `username`: ZestBox-18
  - `locale`: cn（中文）
  - `line_height`: 33
  - `langs_count`: 5（显示前5种语言）

### 3. GitHub 统计卡片
- **技术方案**：使用 github-readme-stats 的 stats API
- **显示内容**：
  - 总提交数
  - 总 PR 数
  - 总 Issue 数
  - 总 Star 数
  - 贡献仓库数

## 布局设计

### 整体结构
```
┌─────────────────────────────────────┐
│         👋 个人介绍区                │
│    "热爱技术的开发者"                │
├─────────────────────────────────────┤
│         🐍 贪吃蛇动画区              │
│    (GitHub贡献图贪吃蛇动画)          │
├─────────────────────────────────────┤
│         📊 统计卡片区                │
│  [语言统计]  [GitHub Stats]          │
│  [Top Languages] [Stats Card]        │
└─────────────────────────────────────┘
```

### 视觉风格
- **主题**：深色主题（dark）
- **配色**：GitHub 默认深色配色
- **布局**：卡片式设计，圆角边框
- **动画**：贪吃蛇 SVG 动画

## 文件结构

```
ZestBox-18/
├── README.md                    # 主页内容
├── .github/
│   └── workflows/
│       └── snake.yml           # 贪吃蛇生成 Action
└── docs/
    └── superpowers/
        └── specs/
            └── 2026-05-02-github-profile-design.md
```

## 技术实现细节

### GitHub Action 配置 (snake.yml)
- **触发条件**：每天 UTC 00:00（定时触发）+ 手动触发
- **运行环境**：ubuntu-latest
- **输出分支**：output
- **输出格式**：SVG

### README.md 内容
1. **个人介绍区**
   - 简短的自我介绍
   - 技术兴趣/专长

2. **贪吃蛇动画区**
   - 引用 output 分支的 SVG
   - 居中显示

3. **统计卡片区**
   - 语言统计卡片
   - GitHub 统计卡片
   - 并排显示

## 兼容性说明
- **浏览器支持**：现代浏览器（Chrome、Firefox、Safari、Edge）
- **移动端**：响应式设计，自动适配
- **加载性能**：使用 SVG 格式，体积小，加载快

## 后续优化方向
1. 添加贡献统计图表
2. 添加技能徽章
3. 添加项目展示区
4. 添加社交链接

---

**设计批准时间**：2026-05-02
**设计状态**：已批准，准备实现