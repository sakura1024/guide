
# WEB前端规范

 [HTML规范]
 [CSS规范]
 [Javascript_ES6_规范]
 [Javascript_React_规范]
# 编辑器配置

 [编辑器配置]
# HTML 规范
## 目录

1. [语法](#language)
1. [HTML5 doctype](#doctype)
1. [编码](#code)
1. [引入CSS和Javascript](#include)
1. [实用高于完美](#pro)
1. [Boolean属性](#boolean)
1. [减少标签数量](#tag)


<a name="language"></a>
## 语法

1. 使用四个空格的缩进
1. 嵌套的节点应该缩进。
1. 在属性上，使用双引号，不要使用单引号。
1. 不要忽略可选的关闭标签（例如，\<\/li> 和 \<\/body>）。

``` HTML
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

<a name="doctype"></a>
## HTML5 doctype

在每个 HTML 页面开头使用这个简单地 doctype 来启用标准模式，使其每个浏览器中尽可能一致的展现。

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

<a name="code"></a>
## 编码

通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式。这样做之后，需要避免在 HTML 中出现字符实体，直接提供字符与文档一致的编码（通常是 UTF-8）。

```html
<head>
  <meta charset="UTF-8">
</head>
```


<a name="include"></a>
## 引入CSS和Javascript

根据 HTML5 规范, 通常在引入 CSS 和 JavaScript 时不需要指明 type，因为 text/css 和 text/javascript 分别是他们的默认值。

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```



<a name="pro"></a>
## 实用高于完美

尽量遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价。任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。



<a name="boolean"></a>
## Boolean属性

Boolean 属性指不需要声明取值的属性。XHTML 需要每个属性声明取值，但是 HTML5 并不需要，不要为 Boolean 属性添加取值

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```



<a name="tag"></a>
## 减少标签数量

在编写 HTML 代码时，需要尽量避免多余的父节点。很多时候，需要通过迭代和重构来使 HTML 变得更少。 参考下面的示例:

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

# Sass Css 规范

来至airbnb的css guide

## 目录

  1. [术语](#terminology)
    - [规则声明](#rule-declaration)
    - [选择器](#selectors)
    - [属性](#properties)
  1. [CSS](#css)
    - [格式](#formatting)
    - [注释](#comments)
    - [OOCSS 和 BEM](#oocss-and-bem)
    - [ID 选择器](#id-selectors)
    - [JavaScript 钩子](#javascript-hooks)
    - [边框](#border)
  1. [Sass](#sass)
    - [语法](#syntax)
    - [排序](#ordering-of-property-declarations)
    - [变量](#variables)
    - [Mixins](#mixins)
    - [扩展指令](#extend-directive)
    - [嵌套选择器](#nested-selectors)

<a name="terminology"></a>
## 术语

<a name="rule-declaration"></a>
### 规则声明

我们把一个（或一组）选择器和一组属性称之为 “规则声明”。举个例子：

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

<a name="selectors"></a>
### 选择器

在规则声明中，“选择器” 负责选取 DOM 树中的元素，这些元素将被定义的属性所修饰。选择器可以匹配 HTML 元素，也可以匹配一个元素的类名、ID, 或者元素拥有的属性。以下是选择器的例子：

```css
.my-element-class {
  /* ... */
}

[aria-hidden] {
  /* ... */
}
```

<a name="properties"></a>
### 属性

最后，属性决定了规则声明里被选择的元素将得到何种样式。属性以键值对形式存在，一个规则声明可以包含一或多个属性定义。以下是属性定义的例子：

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
}
```

<a name="css"></a>
## CSS

<a name="formatting"></a>
### 格式

* 使用 4 个空格作为缩进。
* 类名建议使用破折号代替驼峰法。如果你使用 BEM，也可以使用下划线（参见下面的 [OOCSS 和 BEM](#oocss-and-bem)）。
* 不要使用 ID 选择器。
* 在一个规则声明中应用了多个选择器时，每个选择器独占一行。
* 在规则声明的左大括号 `{` 前加上一个空格。
* 在属性的冒号 `:` 后面加上一个空格，前面不加空格。
* 规则声明的右大括号 `}` 独占一行。
* 规则声明之间用空行分隔开。

**Bad**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**Good**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

<a name="comments"></a>
### 注释

* 建议使用行注释 (在 Sass 中是 `//`) 代替块注释。
* 建议注释独占一行。避免行末注释。
* 给没有自注释的代码写上详细说明，比如：
  - 为什么用到了 z-index
  - 兼容性处理或者针对特定浏览器的 hack

<a name="oocss-and-bem"></a>
### OOCSS 和 BEM

出于以下原因，我们鼓励使用 OOCSS 和 BEM 的某种组合：

  * 可以帮助我们理清 CSS 和 HTML 之间清晰且严谨的关系。
  * 可以帮助我们创建出可重用、易装配的组件。
  * 可以减少嵌套，降低特定性。
  * 可以帮助我们创建出可扩展的样式表。

**OOCSS**，也就是 “Object Oriented CSS（面向对象的CSS）”，是一种写 CSS 的方法，其思想就是鼓励你把样式表看作“对象”的集合：创建可重用性、可重复性的代码段让你可以在整个网站中多次使用。

参考资料：

  * Nicole Sullivan 的 [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine 的 [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**BEM**，也就是 “Block-Element-Modifier”，是一种用于 HTML 和 CSS 类名的_命名约定_。BEM 最初是由 Yandex 提出的，要知道他们拥有巨大的代码库和可伸缩性，BEM 就是为此而生的，并且可以作为一套遵循 OOCSS 的参考指导规范。

  * CSS Trick 的 [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts 的 [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

**示例**

```html
<article class="listing-card listing-card--featured">

  <h1 class="listing-card__title">Adorable 2BR in the sunny Mission</h1>

  <div class="listing-card__content">
    <p>Vestibulum id ligula porta felis euismod semper.</p>
  </div>

</article>
```

```css
.listing-card { }
.listing-card--featured { }
.listing-card__title { }
.listing-card__content { }
```

  * `.listing-card` 是一个块（block），表示高层次的组件。
  * `.listing-card__title` 是一个元素（element），它属于 `.listing-card` 的一部分，因此块是由元素组成的。
  * `.listing-card--featured` 是一个修饰符（modifier），表示这个块与 `.listing-card` 有着不同的状态或者变化。

<a name="id-selectors"></a>
### ID 选择器

在 CSS 中，虽然可以通过 ID 选择元素，但大家通常都会把这种方式列为反面教材。ID 选择器给你的规则声明带来了不必要的高[优先级](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)，而且 ID 选择器是不可重用的。

想要了解关于这个主题的更多内容，参见 [CSS Wizardry 的文章](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/)，文章中有关于如何处理优先级的内容。

<a name="javascript-hooks"></a>
### JavaScript 钩子

避免在 CSS 和 JavaScript 中绑定相同的类。否则开发者在重构时通常会出现以下情况：轻则浪费时间在对照查找每个要改变的类，重则因为害怕破坏功能而不敢作出更改。

我们推荐在创建用于特定 JavaScript 的类名时，添加 `.js-` 前缀：

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

<a name="border"></a>
### 边框

在定义无边框样式时，使用 `0` 代替 `none`。

**Bad**

```css
.foo {
  border: none;
}
```

**Good**

```css
.foo {
  border: 0;
}
```

<a name="sass"></a>
## Sass

<a name="syntax"></a>
### 语法

* 使用 `.scss` 的语法，不使用 `.sass` 原本的语法。
* CSS 和 `@include` 声明按照以下逻辑排序（参见下文）

<a name="ordering-of-property-declarations"></a>
### 属性声明的排序

1. 属性声明

    首先列出除去 `@include` 和嵌套选择器之外的所有属性声明。

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

2. `@include` 声明

    紧随后面的是 `@include`，这样可以使得整个选择器的可读性更高。

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

3. 嵌套选择器

    _如果有必要_用到嵌套选择器，把它们放到最后，在规则声明和嵌套选择器之间要加上空白，相邻嵌套选择器之间也要加上空白。嵌套选择器中的内容也要遵循上述指引。

    ```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);

      .icon {
        margin-right: 10px;
      }
    }
    ```

<a name="variables"></a>
### 变量

变量名应使用破折号（例如 `$my-variable`）代替 camelCased 和 snake_cased 风格。对于仅用在当前文件的变量，可以在变量名之前添加下划线前缀（例如 `$_my-variable`）。

<a name="mixins"></a>
### Mixins

为了让代码遵循 DRY 原则（Don't Repeat Yourself）、增强清晰性或抽象化复杂性，应该使用 mixin，这与那些命名良好的函数的作用是异曲同工的。虽然 mixin 可以不接收参数，但要注意，假如你不压缩负载（比如通过 gzip），这样会导致最终的样式包含不必要的代码重复。

<a name="extend-directive"></a>
### 扩展指令

应避免使用 `@extend` 指令，因为它并不直观，而且具有潜在风险，特别是用在嵌套选择器的时候。即便是在顶层占位符选择器使用扩展，如果选择器的顺序最终会改变，也可能会导致问题。（比如，如果它们存在于其他文件，而加载顺序发生了变化）。其实，使用 @extend 所获得的大部分优化效果，gzip 压缩已经帮助你做到了，因此你只需要通过 mixin 让样式表更符合 DRY 原则就足够了。

<a name="nested-selectors"></a>
### 嵌套选择器

**请不要让嵌套选择器的深度超过 3 层！**

```scss
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```

当遇到以上情况的时候，你也许是这样写 CSS 的：

* 与 HTML 强耦合的（也是脆弱的）*—或者—*
* 过于具体（强大）*—或者—*
* 没有重用


再说一遍: **永远不要嵌套 ID 选择器！**

如果你始终坚持要使用 ID 选择器（劝你三思），那也不应该嵌套它们。如果你正打算这么做，你需要先重新检查你的标签，或者指明原因。如果你想要写出风格良好的 HTML 和 CSS，你是**不**应该这样做的。

