# StudyClick（点击式学习系统）

> 一个轻量级、支持离线运行的多学科点击式刷题系统

---

## 项目简介

**StudyClick** 是一个基于浏览器的开源刷题系统，专为学生自主练习设计。无需输入（化学填空除外），只需点击选项即可完成答题。

- 打开即用，无需安装
- 支持完全离线运行
- 每次随机生成试卷，避免重复练习
- 易扩展，支持多学科内容

---

## 功能特点

### 刷题系统
- 每次打开/刷新随机生成试卷
- 可选题量（10/15/20/30 题）
- 点击即可作答，无需输入
- 即时判分：
  - 正确 → 绿色标记
  - 错误 → 红色标记，同时显示正确答案
- 进度条实时显示答题进度
- 同一题不可重复作答

### 成绩统计
- 自动统计总题数、正确题数、正确率
- 按正确率显示评级（满分/优秀/良好/及格/加油）
- 结果面板带淡入动画

### 错题本
- 英语科目自动记录答错单词
- 使用浏览器本地存储（localStorage）
- 关闭页面后仍然保留
- 支持一键清空

---

## 项目结构

```
StudyClick/
├── index.html                  # 学科选择主页
├── README.md                   # 项目说明
├── STYLE_GUIDE.md              # 样式规范文档
├── ch_list.html                # 化学题库转换工具
├── list.html                   # 英语词表转换工具
├── subjects/
│   ├── 2nd/                    # 新一代题型（此次未修改）
│   │   ├── word-quiz.html      # 英语单词抽测（样式模板）
│   │   ├── english-1-330-基础.html
│   │   ├── english-1-330-进阶.html
│   │   └── english-*.html      # 分段英语文件
│   ├── chinese.html            # 语文古诗测试
│   ├── english287.html         # 英语 1-287 基础版
│   ├── english-287-advanced.html # 英语 1-287 进阶版
│   ├── english288-388.html     # 英语 288-388
│   ├── english432-550.html     # 英语 432-550
│   ├── math.html               # 初三数学核心知识点
│   ├── physics.html            # 初中物理公式
│   └── chemistry.html          # 化学方程式配平/下标填空
```

---

## 使用方法

1. 克隆项目：
```bash
git clone https://github.com/supermastergui/StudyClick.git
```

2. 用浏览器打开 `index.html` 选择学科

3. 或在浏览器中直接打开任意 `subjects/*.html` 文件

---

## 支持学科

| 学科 | 文件 | 题型 |
|------|------|------|
| 英语 | english287.html / english-287-advanced.html / english288-388.html / english432-550.html | 单词释义选择题 |
| 语文 | chinese.html | 古诗文选择题 |
| 数学 | math.html | 知识点选择题 |
| 物理 | physics.html | 公式选择题 |
| 化学 | chemistry.html | 方程式配平填空 |

另有 `subjects/2nd/` 目录包含新一代题型。

---

## 自定义内容

### 添加单词/题目

英语格式（WORD_BANK）：
```javascript
const WORD_BANK = [
    ["apple", "苹果"],
    ["book", "书"],
    ["run", "跑"]
];
```

通用格式（questionBank）：
```javascript
const questionBank = [
    {
        q: "水的化学式是什么？",
        a: "H₂O",
        options: ["H₂O", "CO₂", "NaCl", "O₂"]
    }
];
```

---

## 样式规范

所有页面遵循统一视觉标准，详见 [STYLE_GUIDE.md](STYLE_GUIDE.md)。

核心特点：
- 紫-粉-青三色渐变背景
- 靛蓝主色调（#5c6bc0）
- 白色卡片式题目布局
- 2列选项网格（手机端自动单列）
- 流畅的交互动画

---

## 技术说明

- 纯前端实现，无后端依赖
- HTML5 + CSS3 + 原生 JavaScript
- 响应式设计，适配手机和桌面
- 随机算法：Fisher-Yates 洗牌
- 数据存储：localStorage（错题本）

---

## 后续计划

- [x] 错题专项练习模式
- [ ] 学习数据统计（进度分析）
- [ ] 支持导入 JSON / CSV 数据
- [ ] 界面优化（UI 升级）
- [ ] 移动端适配优化

---

## 贡献指南

欢迎参与贡献：添加新学科、提交题库、优化界面、修复问题。

---

## 开源协议

**Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）**

你可以自由使用、修改和分享，但必须署名并使用相同协议。

协议详情：https://creativecommons.org/licenses/by-sa/4.0/

---

## 作者

作者：supermastergui
