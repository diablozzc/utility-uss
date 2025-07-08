# Utility USS

为Unity样式表提供类似[Tailwind CSS](https://tailwindcss.com)的实用工具类。

## 与Tailwind CSS的区别

1. 不支持半尺寸（例如：`mt-0.5`、`px-3.5`）
2. 类名中的分数转换为单词（例如：`h-1/3` => `h-one-third`）
3. `font-bold`和`font-italic`合并为`font-bold-italic`

## 使用方法

### 完整包使用
将`dist/Utility.uss`复制到您的Unity项目中，并在UXML文档中引用。

### 模块化使用
使用模块化编译功能，您可以选择性地导入所需的功能模块：

```xml
<!-- 仅导入所需的模块 -->
<Style src="project://database/Assets/variables.uss" />
<Style src="project://database/Assets/layout.uss" />
<Style src="project://database/Assets/colors.uss" />
```

或者导入完整的模块化索引：

```xml
<!-- 导入所有模块 -->
<Style src="project://database/Assets/index.uss" />
```

### 示例

```xml
<ui:UXML xmlns:ui="UnityEngine.UIElements" xmlns:uie="UnityEditor.UIElements" xsi="http://www.w3.org/2001/XMLSchema-instance" engine="UnityEngine.UIElements" editor="UnityEditor.UIElements" noNamespaceSchemaLocation="../../UIElementsSchema/UIElements.xsd" editor-extension-mode="False">
  <Style src="project://database/Assets/Utility.uss" />

  <ui:VisualElement class="w-full h-full bg-slate-300 items-center justify-center">
    <ui:VisualElement class="w-48 p-12 text-center">
        <ui:Label text="Hello world!" class="text-slate-900 text-2xl" />
    </ui:VisualElement>
  </ui:VisualElement>
</ui:UXML>
```

## 开发环境

首先确保您的系统已安装nodejs，然后运行：

```bash
npm install
```

### 构建命令

**开发模式（监听文件变化）：**
```bash
npm run dev
```

**生产构建（压缩版本）：**
```bash
npm run build
```

**模块化构建（推荐）：**
```bash
npm run build:modules
```

## 模块化构建功能

我们新增了模块化构建功能，提供更灵活的使用方式：

### 生成的模块文件

运行`npm run build:modules`后，会在`dist/`目录下生成以下文件：

- `variables.uss` - CSS变量定义
- `layout.uss` - 布局相关（显示、定位、盒模型等）
- `flexbox.uss` - Flexbox布局
- `spacing.uss` - 间距相关（边距、宽高等）
- `typography.uss` - 文字排版
- `colors.uss` - 颜色相关
- `borders.uss` - 边框相关
- `backgrounds.uss` - 背景相关
- `transforms.uss` - 变换相关
- `transitions.uss` - 过渡动画
- `effects.uss` - 效果相关（透明度、可见性等）
- `utilities.uss` - 实用工具类
- `index.uss` - 主索引文件（导入所有模块）

### 优化特性

1. **无重复CSS变量**：避免在每个模块中重复定义`:root`变量
2. **清晰的依赖关系**：通过`@import`语句管理模块间的依赖
3. **按需导入**：只导入项目中实际使用的模块
4. **更好的可读性**：未压缩的代码格式，便于调试和理解

### 使用建议

- 小型项目：使用`dist/Utility.uss`（完整包）
- 大型项目：使用模块化构建，按需导入所需模块
- 性能优化：仅导入使用的模块以减少文件大小

## 未实现的功能

以下USS属性尚未实现：

```
-unity-slice-bottom
-unity-slice-left
-unity-slice-right
-unity-slice-scale
-unity-slice-top
```

## 说明

本项目与[Tailwind CSS](https://tailwindcss.com)官方无任何关联。我只是喜欢在Web项目中使用Tailwind CSS，希望能在Unity中使用类似的工具。