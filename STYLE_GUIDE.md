# StudyClick 样式规范

> 基于 `subjects/2nd/word-quiz.html` 确立的统一视觉标准。
> 所有 `subjects/2nd/` 以外的 `.html` 文件均应遵循此规范。

---

## 1. 色彩体系

| 用途 | 色值 | 说明 |
|------|------|------|
| 页面背景 | `linear-gradient(135deg, #e8eaf6 0%, #fce4ec 50%, #e0f2f1 100%)` | 紫-粉-青三色渐变 |
| 卡片/面板背景 | `#fff` | 纯白 |
| 主色调 | `#5c6bc0` | 靛蓝色，按钮、进度条、数字高亮 |
| 主色调hover | `#3f51b5` | 深靛蓝 |
| 正确色 | `#c8e6c9` 背景 / `#4caf50` 边框 / `#1b5e20` 文字 | 绿色系 |
| 错误色 | `#ffcdd2` 背景 / `#f44336` 边框 / `#b71c1c` 文字 | 红色系 |
| 满分 | `#c8e6c9` / `#1b5e20` | 100% |
| 优秀 | `#c8e6c9` / `#2e7d32` | 90-99% |
| 良好 | `#fff9c4` / `#f57f17` | 70-89% |
| 一般 | `#ffe0b2` / `#e65100` | 60-69% |
| 加油 | `#ffcdd2` / `#b71c1c` | <60% |
| 重置按钮 | `#ef5350` / hover `#d32f2f` | 红色 |
| 返回按钮 | `#78909c` / hover `#546e7a` | 灰蓝 |
| 次要文字 | `#888` | 副标题、标签 |
| 页脚文字 | `#aaa` | 极淡 |
| 进度条底色 | `#e0e0e0` | 浅灰 |
| 进度条填充 | `linear-gradient(90deg, #5c6bc0, #26c6da)` | 靛蓝到青 |
| 序号圆圈 | bg `#e8eaf6` / color `#5c6bc0` | 淡紫底靛蓝字 |
| 题目高亮 | `#1a237e` | 深靛蓝 |
| 选项边框 | `#e0e0e0` 默认 / `#5c6bc0` hover | |
| 选项背景 | `#fafafa` 默认 / `#e8eaf6` hover | |

---

## 2. 排版

| 属性 | 值 |
|------|-----|
| 全局字体 | `"Segoe UI", "Microsoft YaHei", sans-serif` |
| 全局盒模型 | `box-sizing: border-box; margin: 0; padding: 0` |
| body | `min-height: 100vh; padding: 20px` |
| 容器 | `max-width: 780px; margin: 0 auto` |
| h1 | `28px, color #333` |
| 副标题 | `13px, color #888` |
| 题目文字 | `18px / font-weight 600` |
| 选项文字 | `15px` |
| 统计数字 | `32px / font-weight 700` |
| 评级标签 | `18px / font-weight 600` |

---

## 3. 页面结构

```
.container (max-width: 780px)
  ├── .header          — 标题 h1 + .subtitle
  ├── .control-bar     — 题量选择 + 操作按钮
  ├── .progress-wrap   — .progress-text + .progress-bar > .progress-fill
  ├── #quiz            — 题目列表
  ├── .result-panel    — 结果统计(初始 display:none)
  └── .footer          — 版权信息
```

---

## 4. 组件规格

### 4.1 控制栏按钮

```css
.btn-start  { background: #5c6bc0; color: #fff; }  /* hover: #3f51b5 */
.btn-reset  { background: #ef5350; color: #fff; }  /* hover: #d32f2f */
.btn-home   { background: #78909c; color: #fff; }  /* hover: #546e7a */
```
通用: `padding: 9px 22px; border-radius: 20px; font-size: 14px; font-weight: 500`

### 4.2 题目卡片

```css
.question {
    background: #fff;  padding: 18px 20px;  margin-bottom: 14px;
    border-radius: 14px;  box-shadow: 0 2px 12px rgba(0,0,0,0.06);
}
.question:hover { box-shadow: 0 4px 20px rgba(0,0,0,0.10); }
```

### 4.3 序号圆圈

```css
.q-num {
    display: inline-flex;  width: 28px;  height: 28px;  border-radius: 50%;
    background: #e8eaf6;  color: #5c6bc0;
    font-size: 13px;  font-weight: 700;
}
```

### 4.4 选项网格

- 桌面: `grid-template-columns: 1fr 1fr; gap: 8px`
- 手机(≤500px): `grid-template-columns: 1fr`

### 4.5 选项按钮

```css
.option-btn {
    width: 100%;  padding: 11px 14px;
    border: 2px solid #e0e0e0;  border-radius: 10px;
    background: #fafafa;  font-size: 15px;  text-align: center;
    cursor: pointer;  transition: all 0.18s;
}
.option-btn:hover   { border-color: #5c6bc0; background: #e8eaf6; }
.option-btn:active  { transform: scale(0.97); }
.option-btn.correct { background: #c8e6c9!important; border-color: #4caf50!important; color: #1b5e20!important; font-weight: 600; }
.option-btn.wrong   { background: #ffcdd2!important; border-color: #f44336!important; color: #b71c1c!important; }
```

### 4.6 已答题状态

```css
.question.done .option-btn        { cursor: default; opacity: 0.75; }
.question.done .option-btn.correct { opacity: 1; }
.question.done .option-btn.wrong   { opacity: 0.7; }
```

### 4.7 结果面板

- 默认隐藏，显示时加 `.show` + `fadeUp` 动画(0.4s)
- 统计: flex 居中, gap 32px
- 评级徽章: `border-radius: 20px; padding: 8px 20px`

### 4.8 成绩评级

| 正确率 | 文案 | CSS类 |
|--------|------|-------|
| 100% | 🏆 满分！太厉害了！ | grade-perfect |
| 90-99% | 🌟 优秀！继续保持！ | grade-excellent |
| 70-89% | 👍 良好，还有进步空间 | grade-good |
| 60-69% | 📚 及格，继续加油 | grade-fair |
| <60% | 💪 加油，多练习就会进步 | grade-poor |

---

## 5. 主页特殊样式 (index.html)

主页使用卡片网格，保留差异化：

- 容器: `max-width: 1000px`
- 网格: `repeat(auto-fit, minmax(220px, 1fr))`
- 卡片: `border-radius: 16px; padding: 25px`
- 卡片hover: `translateY(-6px)`
- 图标: `40px`
- 使用与刷题页相同的配色和字体

---

## 6. 文件范围

**需改造**: `index.html`, `subjects/english287.html`, `subjects/english-287-advanced.html`, `subjects/english288-388.html`, `subjects/english432-550.html`, `subjects/chinese.html`, `subjects/math.html`, `subjects/physics.html`, `subjects/chemistry.html`, `ch_list.html`, `list.html`

**保持不变**: `subjects/2nd/` 下所有文件
