# 个人简历网站 实现计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 构建零依赖、响应式、科技蓝工科风个人简历单页网站，单个 HTML 文件保存即用

**Architecture:** 单 HTML 文件，CSS/JS 全内联。960px 居中布局，6 大模块卡片（Header/教育/技能/竞赛/项目/自我评价）。移动端 768px/480px 双断点响应式适配。关键词自动高亮 JavaScript 引擎。

**Tech Stack:** HTML5 + CSS3 + Vanilla JS，零外部依赖

## Global Constraints

- 零外部依赖：无 CDN、无 npm 包、无外部字体/图标库
- 所有 Unicode 图标（📞✉📍🔧🌐📋🚗🥉🥈📁）直接使用 emoji，不引入 icon font
- 照片路径 `assets/photo.jpg`，提供 CSS fallback 字母头像
- 关键词列表：STM32、MSPM0、PID、OpenMV、Python、Keil5、CubeMX、IIC、USART、SPI、C51、TI、ARM、单片机、嵌入式
- 配色：科技蓝 #1a6fc4、深灰 #2d3436、浅灰底 #f5f6fa、卡片白 #ffffff、标签底 #e8f0fe、注释绿 #6a9955
- 桌面端最大宽度 960px，移动端断点 768px 和 480px

---

### Task 1: 项目搭建 — 目录结构与基础 HTML 骨架

**Files:**
- Create: `resume.html`
- Create: `assets/` (directory)
- Create: `assets/photo.jpg` (placeholder)

**Interfaces:**
- Consumes: 无
- Produces: `resume.html` — 完整 HTML 骨架（doctype → footer），后续任务在此文件上增量修改

- [ ] **Step 1: 创建 assets 目录和照片占位说明**

```bash
mkdir -p assets
echo "请将您的个人照片命名为 photo.jpg 放入 assets 目录" > assets/README.txt
```

- [ ] **Step 2: 创建 resume.html 基础骨架**

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>赵英琦 — 嵌入式开发工程师</title>
    <style>
        /* CSS placeholder — Task 4-5 填充 */
    </style>
</head>
<body>
    <!-- HTML placeholder — Task 2-3 填充 -->
    <script>
        // JS placeholder — Task 6 填充
    </script>
</body>
</html>
```

```bash
open resume.html  # 确认空白页面在浏览器中正常打开
```

- [ ] **Step 3: 初始化 git 提交**

```bash
git add assets/ resume.html
git commit -m "feat: scaffold project structure and HTML skeleton"
```

---

### Task 2: HTML 结构 — Header + 教育经历

**Files:**
- Modify: `resume.html` — 替换 `<body>` 中的 placeholder 为实际结构

**Interfaces:**
- Consumes: Task 1 的 HTML 骨架
- Produces: header + education 两个模块的完整 HTML 结构，后续 CSS 可直接选择器定位

- [ ] **Step 1: 编写 Header 模块 HTML**

替换 `<!-- HTML placeholder -->` 为：

```html
<header class="header">
    <div class="header-inner">
        <div class="avatar-container">
            <img class="avatar" src="assets/photo.jpg" alt="赵英琦" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">
            <div class="avatar-fallback" style="display:none;">赵</div>
        </div>
        <div class="header-text">
            <h1 class="name">赵英琦</h1>
            <p class="subtitle">嵌入式开发 · 机器人工程</p>
            <div class="contact-bar">
                <span>📞 18108518572</span>
                <span>✉ 2019855865@qq.com</span>
                <span>📍 山东省青岛市黄岛区</span>
            </div>
        </div>
    </div>
    <div class="code-decoration top-decoration">// aspiring embedded engineer</div>
</header>
```

- [ ] **Step 2: 编写教育经历模块 HTML**

```html
<section class="module" id="education">
    <div class="module-header">
        <div class="module-bar"></div>
        <h2>教育经历</h2>
    </div>
    <div class="module-body">
        <div class="edu-meta">
            <span class="edu-school">青岛理工大学</span>
            <span class="edu-major">机器人工程 本科</span>
            <span class="edu-gpa">GPA 3.8</span>
        </div>
        <p class="edu-time">2023/09 - 至今</p>
        <div class="course-tags">
            <span class="tag">C语言程序设计</span>
            <span class="tag">电路原理</span>
            <span class="tag">模拟与数字电路</span>
            <span class="tag">微型计算机系统</span>
            <span class="tag">Linux操作系统</span>
            <span class="tag">电力电子技术</span>
            <span class="tag">自动控制原理</span>
            <span class="tag">现代控制理论</span>
            <span class="tag">机器人检测技术</span>
        </div>
    </div>
</section>
```

- [ ] **Step 3: 浏览器验证 HTML 结构**

```bash
open resume.html  # 确认 header 和 education 模块在浏览器中可见（无样式裸结构）
```

- [ ] **Step 4: 提交**

```bash
git add resume.html
git commit -m "feat: add header and education HTML structure"
```

---

### Task 3: HTML 结构 — 技能 + 竞赛 + 项目 + 自我评价 + Footer

**Files:**
- Modify: `resume.html` — 头部之后插入剩余模块 HTML

**Interfaces:**
- Consumes: Task 2 的 header + education 模块
- Produces: 完整 6 模块 + footer 的 HTML 结构

- [ ] **Step 1: 编写技能证书模块 HTML**

```html
<section class="module" id="skills">
    <div class="module-header">
        <div class="module-bar"></div>
        <h2>技能证书</h2>
    </div>
    <div class="module-body">
        <div class="skill-category">
            <h3>🔧 嵌入式硬件</h3>
            <div class="skill-tags">
                <span class="tag tag-hardware">STM32F4/F7/G4/H7</span>
                <span class="tag tag-hardware">C51</span>
                <span class="tag tag-hardware">TI MSPM0</span>
                <span class="tag tag-hardware">Keil5</span>
                <span class="tag tag-hardware">CubeMX</span>
                <span class="tag tag-hardware">IIC</span>
                <span class="tag tag-hardware">USART</span>
                <span class="tag tag-hardware">SPI</span>
                <span class="tag tag-hardware">示波器</span>
                <span class="tag tag-hardware">万用表</span>
            </div>
        </div>
        <div class="skill-category">
            <h3>🌐 语言证书</h3>
            <p class="skill-line">大学英语四级 · 大学英语六级</p>
        </div>
        <div class="skill-category">
            <h3>📋 办公技能</h3>
            <p class="skill-line">Word · Excel · PPT</p>
        </div>
        <div class="skill-category">
            <h3>🚗 通用证书</h3>
            <p class="skill-line">C1驾驶证</p>
        </div>
    </div>
</section>
```

- [ ] **Step 2: 编写竞赛荣誉模块 HTML**

```html
<section class="module" id="competitions">
    <div class="module-header">
        <div class="module-bar"></div>
        <h2>竞赛荣誉</h2>
    </div>
    <div class="module-body">
        <div class="comp-entry">
            <span class="comp-medal">🥉</span>
            <div>
                <p class="comp-name">全国大学生电子设计竞赛</p>
                <p class="comp-detail">山东赛区三等奖 · 2025/07 - 2025/08</p>
            </div>
        </div>
        <div class="comp-entry">
            <span class="comp-medal">🥈</span>
            <div>
                <p class="comp-name">青岛理工大学第二届电子设计竞赛</p>
                <p class="comp-detail">二等奖 · 2024/10 - 2024/12</p>
            </div>
        </div>
    </div>
</section>
```

- [ ] **Step 3: 编写项目经历模块 HTML**

```html
<section class="module" id="projects">
    <div class="module-header">
        <div class="module-bar"></div>
        <h2>项目经历</h2>
    </div>
    <div class="module-body">
        <div class="project-card">
            <h3>📁 简易自行瞄准装置</h3>
            <p class="project-role">视觉模块和算法调试负责人 · 2025/07 - 2025/08</p>
            <p class="project-desc">
                基于 TI MSPM0 单片机设计并实现自动寻迹与激光瞄准系统；本人全权负责视觉识别模块开发，采用 OpenMV + Python 完成靶心检测、坐标提取与串口数据传输；参与小车循迹 PID 控制算法调试与参数整定；协助完成硬件搭建、双电源独立供电电路设计与整机系统联调；成品实现激光精准瞄准靶心，光斑直径 ≤0.5cm，全部达到赛事设计指标。
            </p>
        </div>
        <div class="project-card">
            <h3>📁 基于图像识别技术的光点运动轨迹控制系统</h3>
            <p class="project-role">控制系统开发和算法负责人 · 2024/10 - 2024/12</p>
            <p class="project-desc">
                基于 STM32 单片机制作激光光点二维控制装置，可在1米距离、50cm×50cm靶纸上完成激光光点精准定位与自定义轨迹运动；本人负责主程序逻辑开发、PID 闭环控制算法编写与调参优化，保障光点定位精度与轨迹平滑跟踪效果满足全部设计指标。
            </p>
        </div>
    </div>
</section>
```

- [ ] **Step 4: 编写自我评价和 Footer HTML**

```html
<section class="module" id="about">
    <div class="module-header">
        <div class="module-bar"></div>
        <h2>自我评价</h2>
    </div>
    <div class="module-body">
        <p class="about-text">
            学习态度端正，动手实践能力突出，深耕嵌入式开发与运动控制算法，具备完整电子竞赛落地项目经验；做事踏实严谨，逻辑思维清晰，编程功底扎实，拥有优秀团队协作与工程实操落地能力；英语读写口语流畅，可无障碍和外籍人士沟通交流。
        </p>
    </div>
</section>

<footer class="footer">
    <div class="code-decoration footer-decoration">/* 2026 · 赵英琦 · embedded &amp; robotics */</div>
</footer>
```

- [ ] **Step 5: 浏览器验证完整 HTML 结构**

```bash
open resume.html  # 确认所有 6 个模块 + footer 在浏览器中可见
```

- [ ] **Step 6: 提交**

```bash
git add resume.html
git commit -m "feat: add remaining modules HTML — skills, competitions, projects, about, footer"
```

---

### Task 4: CSS 样式 — 全局 + Header + 教育经历模块

**Files:**
- Modify: `resume.html` — 替换 `<style>` placeholder 为实际样式

**Interfaces:**
- Consumes: Task 3 完整 HTML 结构
- Produces: 全局样式 + Header + 教育模块的完整视觉呈现

- [ ] **Step 1: 编写 CSS Reset + 全局样式**

```css
/* === Reset & Global === */
*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: "PingFang SC", "Microsoft YaHei", "Helvetica Neue", sans-serif;
    background-color: #f5f6fa;
    color: #2d3436;
    line-height: 1.6;
    min-height: 100vh;
}

.container {
    max-width: 960px;
    margin: 0 auto;
    padding: 32px 20px;
}

/* === Code Decorations === */
.code-decoration {
    font-family: "Consolas", "Monaco", "Courier New", monospace;
    color: #6a9955;
    font-size: 13px;
}

.top-decoration {
    text-align: right;
    margin-top: 8px;
}

/* === Module Shared === */
.module {
    background: #ffffff;
    border-radius: 10px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
    margin-bottom: 24px;
    padding: 28px 32px;
}

.module-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
}

.module-bar {
    width: 3px;
    height: 22px;
    background: #1a6fc4;
    border-radius: 2px;
    flex-shrink: 0;
}

.module-header h2 {
    font-size: 18px;
    font-weight: 700;
    color: #1a6fc4;
}

.module-body {
    padding-left: 15px;
}
```

- [ ] **Step 2: 编写 Header CSS**

```css
/* === Header === */
.header {
    background: #ffffff;
    border-radius: 10px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
    padding: 36px 32px 16px;
    margin-bottom: 24px;
}

.header-inner {
    display: flex;
    align-items: center;
    gap: 24px;
}

.avatar-container {
    position: relative;
    flex-shrink: 0;
}

.avatar {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #1a6fc4;
    display: block;
}

.avatar-fallback {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    background: #1a6fc4;
    color: #fff;
    font-size: 42px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
}

.name {
    font-size: 28px;
    font-weight: 700;
    color: #1a6fc4;
    margin-bottom: 4px;
}

.subtitle {
    font-size: 15px;
    color: #636e72;
    margin-bottom: 12px;
}

.contact-bar {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    font-size: 14px;
    color: #555;
}

.contact-bar span {
    white-space: nowrap;
}
```

- [ ] **Step 3: 编写教育经历 CSS**

```css
/* === Education === */
.edu-meta {
    display: flex;
    align-items: baseline;
    gap: 16px;
    flex-wrap: wrap;
    margin-bottom: 4px;
}

.edu-school {
    font-size: 17px;
    font-weight: 700;
    color: #2d3436;
}

.edu-major {
    font-size: 15px;
    color: #555;
}

.edu-gpa {
    font-size: 15px;
    font-weight: 700;
    color: #1a6fc4;
}

.edu-time {
    font-size: 13px;
    color: #999;
    margin-bottom: 14px;
}

.course-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
}

.tag {
    display: inline-block;
    background: #e8f0fe;
    color: #1a6fc4;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 13px;
    font-weight: 500;
}
```

- [ ] **Step 4: 浏览器验证样式效果**

```bash
open resume.html  # 确认 header + education 模块样式正确
```

- [ ] **Step 5: 提交**

```bash
git add resume.html
git commit -m "style: add global reset, header and education CSS"
```

---

### Task 5: CSS 样式 — 技能 + 竞赛 + 项目 + 自我评价 + Footer + 响应式

**Files:**
- Modify: `resume.html` — CSS 区域追加剩余模块样式和响应式断点

**Interfaces:**
- Consumes: Task 4 的全局 + header + education 样式
- Produces: 完整的 CSS 样式系统，桌面端 + 移动端双断点

- [ ] **Step 1: 编写技能证书 CSS**

```css
/* === Skills === */
.skill-category {
    margin-bottom: 14px;
}

.skill-category:last-child {
    margin-bottom: 0;
}

.skill-category h3 {
    font-size: 15px;
    font-weight: 600;
    color: #2d3436;
    margin-bottom: 8px;
}

.skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
}

.tag-hardware {
    background: #e8f0fe;
    color: #1a6fc4;
    border: 1px solid #bcd4f5;
    font-family: "Consolas", "Monaco", monospace;
    font-size: 12px;
}

.skill-line {
    font-size: 14px;
    color: #555;
}
```

- [ ] **Step 2: 编写竞赛荣誉 CSS**

```css
/* === Competitions === */
.comp-entry {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    margin-bottom: 14px;
}

.comp-entry:last-child {
    margin-bottom: 0;
}

.comp-medal {
    font-size: 28px;
    flex-shrink: 0;
    line-height: 1.3;
}

.comp-name {
    font-size: 16px;
    font-weight: 600;
    color: #2d3436;
    margin-bottom: 2px;
}

.comp-detail {
    font-size: 13px;
    color: #888;
}
```

- [ ] **Step 3: 编写项目经历 CSS**

```css
/* === Projects === */
.project-card {
    background: #fafbfc;
    border: 1px solid #eee;
    border-radius: 8px;
    padding: 20px 24px;
    margin-bottom: 16px;
}

.project-card:last-child {
    margin-bottom: 0;
}

.project-card h3 {
    font-size: 17px;
    font-weight: 700;
    color: #2d3436;
    margin-bottom: 4px;
}

.project-role {
    font-size: 13px;
    color: #888;
    margin-bottom: 12px;
}

.project-desc {
    font-size: 14px;
    color: #444;
    line-height: 1.8;
}

.project-desc strong {
    color: #1a6fc4;
    font-weight: 700;
    font-family: "Consolas", "Monaco", monospace;
    font-size: 13px;
    background: #e8f0fe;
    padding: 1px 6px;
    border-radius: 3px;
}
```

- [ ] **Step 4: 编写自我评价 + Footer CSS**

```css
/* === About === */
.about-text {
    font-size: 15px;
    color: #444;
    line-height: 1.9;
}

/* === Footer === */
.footer {
    text-align: center;
    padding: 12px 0 32px;
}

.footer-decoration {
    font-size: 12px;
    opacity: 0.6;
}
```

- [ ] **Step 5: 编写响应式 CSS**

```css
/* === Responsive === */
@media (max-width: 768px) {
    .container {
        padding: 20px 12px;
    }

    .header {
        padding: 28px 20px 12px;
    }

    .header-inner {
        flex-direction: column;
        text-align: center;
    }

    .avatar, .avatar-fallback {
        width: 96px;
        height: 96px;
    }

    .contact-bar {
        justify-content: center;
        gap: 10px;
    }

    .name {
        font-size: 24px;
    }

    .module {
        padding: 20px;
        margin-bottom: 16px;
    }

    .module-body {
        padding-left: 0;
    }

    .edu-meta {
        flex-direction: column;
        gap: 2px;
    }

    .course-tags .tag {
        font-size: 12px;
        padding: 3px 10px;
    }

    .project-card {
        padding: 16px;
    }

    .top-decoration {
        text-align: center;
    }
}

@media (max-width: 480px) {
    .name {
        font-size: 22px;
    }

    .subtitle {
        font-size: 14px;
    }

    .contact-bar {
        font-size: 13px;
        gap: 6px;
    }

    .module {
        padding: 16px;
    }

    .module-header h2 {
        font-size: 16px;
    }

    .comp-medal {
        font-size: 24px;
    }

    .project-card h3 {
        font-size: 15px;
    }

    .project-desc {
        font-size: 13px;
    }

    .skill-tags .tag {
        font-size: 11px;
        padding: 3px 8px;
    }

    .course-tags {
        gap: 6px;
    }
}
```

- [ ] **Step 6: 浏览器验证完整桌面端和移动端样式**

```bash
open resume.html  # 确认桌面端样式完整；缩小浏览器窗口测试 768px 和 480px 断点
```

- [ ] **Step 7: 提交**

```bash
git add resume.html
git commit -m "style: add skills, competitions, projects, about, footer CSS and responsive breakpoints"
```

---

### Task 6: JavaScript — 关键词自动高亮 + 照片降级

**Files:**
- Modify: `resume.html` — 替换 `<script>` placeholder 为实际逻辑

**Interfaces:**
- Consumes: Task 5 完整 CSS（依赖 `.project-desc` 内文本内容和 `strong` 样式）
- Produces: 页面加载时自动对项目描述中的关键词进行 `<strong>` 包裹高亮；照片加载失败时显示字母头像

- [ ] **Step 1: 编写关键词高亮 JavaScript**

```javascript
// === Keyword Auto-Highlight ===
(function() {
    var KEYWORDS = [
        'STM32', 'MSPM0', 'PID', 'OpenMV', 'Python',
        'Keil5', 'CubeMX', 'IIC', 'USART', 'SPI', 'C51',
        'TI', 'ARM', '单片机', '嵌入式'
    ];

    var descEls = document.querySelectorAll('.project-desc');
    descEls.forEach(function(el) {
        var html = el.innerHTML;
        KEYWORDS.forEach(function(kw) {
            // 匹配不在 HTML 标签内的关键词，用 word boundary
            var pattern = new RegExp('(?!<[^>]*)(' + kw.replace(/[-\/\\^$*+?.()|[\]{}]/g, '\\$&') + ')(?![^<]*>)', 'gi');
            html = html.replace(pattern, '<strong>$1</strong>');
        });
        el.innerHTML = html;
    });
})();
```

- [ ] **Step 2: 编写照片降级逻辑 + DOMContentLoaded 保证**

照片降级已在 HTML 的 `onerror` 中实现。JS 侧做兜底：

```javascript
// === Photo Fallback (belt-and-suspenders) ===
document.addEventListener('DOMContentLoaded', function() {
    var avatar = document.querySelector('.avatar');
    var fallback = document.querySelector('.avatar-fallback');
    if (avatar && fallback && !avatar.complete) {
        // img hasn't loaded yet — onerror will handle
    }
    if (avatar && fallback && avatar.naturalWidth === 0 && avatar.complete) {
        avatar.style.display = 'none';
        fallback.style.display = 'flex';
    }
});
```

- [ ] **Step 3: 浏览器验证关键词高亮和照片降级**

```bash
open resume.html  # 确认项目描述中 STM32、PID、OpenMV 等关键词已高亮；确认照片或降级字母头像正常显示
```

- [ ] **Step 4: 提交**

```bash
git add resume.html
git commit -m "feat: add keyword auto-highlighting and photo fallback JS"
```

---

### Task 7: 最终验证与清理

**Files:**
- Modify: `assets/README.txt` — 更新使用说明
- Verify: `resume.html` — 全平台验证

- [ ] **Step 1: 更新使用说明**

```bash
cat > assets/README.txt << 'EOF'
个人简历网站使用说明
====================

1. 将您的个人照片命名为 photo.jpg，放入 assets 目录覆盖占位文件
2. 用浏览器打开 resume.html 即可查看
3. 如需修改内容，用文本编辑器编辑 resume.html 中的文字

技术说明：
- 零依赖，单文件，保存即用
- 支持桌面端和移动端响应式浏览
- 项目经历中的技术关键词自动高亮
EOF
```

- [ ] **Step 2: 桌面端浏览器测试**

```bash
open resume.html  # Chrome/Firefox/Edge 验证全部 6 模块显示正确
```

- [ ] **Step 3: 移动端视口模拟测试**

```bash
# 在浏览器开发者工具中切换移动视图 (iPhone 14 / Pixel 7)
# 验证：头像居中、模块折叠、标签网格1-2列、字号舒适
```

- [ ] **Step 4: 最终提交**

```bash
git add assets/README.txt
git commit -m "docs: add usage instructions and finalize resume website"
```

---

## 执行说明

所有任务顺序执行（Task 1 → Task 2 → ... → Task 7），每个任务修改同一文件 `resume.html`，逐层叠加 HTML → CSS → JS。每个任务结束后提交，确保任意时刻代码可回滚。
