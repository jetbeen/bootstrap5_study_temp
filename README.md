# bootstrap5_temp
# 在 Bootstrap 导航栏中添加三级菜单

你希望在已有的二级菜单基础上，为导航栏添加**三级菜单**功能，同时明确指出具体的修改位置和修改方式，保持 Bootstrap 5.1.3 技术栈和整体视觉风格不变。

### 实现思路

1. 基于 Bootstrap 5.1.3 扩展下拉菜单组件，实现三级嵌套菜单

2. 为指定的二级菜单项添加三级菜单结构和触发逻辑

3. 自定义三级菜单的样式，保证视觉层级清晰

4. 优化移动端适配，确保三级菜单在小屏设备上正常交互

### 完整修改后代码

详情见： dydfgj-home 1.1.0.html
原始代码： dydfgj-home.html

### 核心修改位置及说明

#### 1. CSS 样式新增/修改（`<style>` 标签内）

|修改位置|修改内容|作用|
|---|---|---|
|新增 `.dropdown-submenu` 样式|`.dropdown-submenu { position: relative; }`|定义三级菜单容器的定位方式|
|新增三级菜单定位样式|`.dropdown-submenu .dropdown-menu { top: 0; left: 100%; margin-top: -5px !important; display: none; }`|三级菜单向右展开，定位在二级菜单右侧|
|新增 hover 触发样式|`.dropdown-submenu:hover > .dropdown-menu { display: block; }`|鼠标悬浮时显示三级菜单|
|修改 `.dropdown-item` 样式|添加 `display: flex; justify-content: space-between; align-items: center;`|为三级菜单箭头预留位置，优化布局|
|新增三级菜单箭头样式|`.dropdown-submenu > .dropdown-item::after { content: "\f105"; font-family: "bootstrap-icons"; font-size: 12px; margin-left: 10px; transition: transform 0.3s ease; }`|为有三级菜单的菜单项添加右箭头|
|新增箭头动画|`.dropdown-submenu:hover > .dropdown-item::after { transform: translateX(5px); }`|鼠标悬浮时箭头右移，增强交互反馈|
|移动端响应式修改|新增 `.dropdown-submenu .dropdown-menu { left: 0 !important; top: auto !important; margin-left: 20px !important; }`|移动端三级菜单向下展开，而非向右|
#### 2. HTML 结构修改（导航栏部分）

在「典当服务」的二级菜单中，为需要三级菜单的项添加嵌套结构：

```HTML

<!-- 原二级菜单项 -->
<li><a class="dropdown-item" href="#">房产典当</a></li>

<!-- 修改为三级菜单结构 -->
<li class="dropdown-submenu">
    <a class="dropdown-item" href="#">房产典当</a>
    <ul class="dropdown-menu">
        <li><a class="dropdown-item" href="#">住宅典当</a></li>
        <li><a class="dropdown-item" href="#">商铺典当</a></li>
        <li><a class="dropdown-item" href="#">写字楼典当</a></li>
        <li><a class="dropdown-item" href="#">别墅典当</a></li>
    </ul>
</li>
```

#### 3. JS 脚本微调

修改了「点击外部关闭下拉菜单」的逻辑，适配三级菜单结构：

```JavaScript

// 原逻辑
const toggle = dropdown.previousElementSibling;

// 修改后
const toggle = dropdown.closest('.dropdown').querySelector('.dropdown-toggle');
```

### 总结

1. **核心修改点**：

    - 新增 `dropdown-submenu` 类及相关 CSS 样式，实现三级菜单的定位和触发

    - 为「房产典当」「汽车典当」「奢侈品典当」添加三级菜单嵌套结构

    - 优化移动端三级菜单展示方式，适配小屏设备

    - 增加三级菜单箭头标识和交互动画，提升用户体验

2. **关键特性**：

    - 桌面端：三级菜单向右悬浮展开，有箭头动画反馈

    - 移动端：三级菜单向下展开，自动缩进，适配折叠导航

    - 完全基于 CSS 实现，无需额外 JS 插件，兼容性好

    - 保持原有页面的所有功能和样式，仅扩展导航层级

3. **扩展说明**：

如需为其他导航项添加三级菜单，只需复用 `dropdown-submenu` 结构，并确保 CSS 样式生效即可，代码结构具备良好的可扩展性。
> （注：文档部分内容可能由 AI 生成）

