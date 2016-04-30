从零开始写一个页面，绝大多数情况下我们都需要一个代码样板来帮我们快速开始，避免重复的工作。这个样板至少会包括以下内容：

1. 设置 doctype
1. 设置页面编码
1. 引入初始化 css

作为一个前端开发者，你应该维护好一份适合自己的代码样板，使得日后自己的每个项目都可以以此来初始化。下面是一份我常用的样板(index.html)：
```html

    <!--
    HTML5. Use tags like <article>, <section>, etc.
    See: http://www.sitepoint.com/web-foundations/doctypes/
    -->
    <!doctype html>

    <html lang="en">
      <head>
        <meta charset="utf-8">

        <!--
        Ask IE to behave like a modern browser
        See: https://www.modern.ie/en-us/performance/how-to-use-x-ua-compatible
        -->
        <meta http-equiv="x-ua-compatible" content="ie=edge">

        <title>My Site</title>

        <!--
        Disables zooming on mobile devices.
        -->
        <meta name="viewport" content="width=device-width,initial-scale=1">

        <!--
        Stylesheet that minimizes browser differences.
        See: http://necolas.github.io/normalize.css/
        -->
        <link rel="stylesheet" href="css/normalize.css">

        <!--
        Our own stylesheet.
        -->
        <link rel="stylesheet" href="css/main.css">
      </head>
      <body>
        put content here
      </body>
    </html>
```

在这个简单的样板我们做了挺多事：

- 指定使用 HTML5 语法
- 要求 IE 遵守现代浏览器的渲染标准
- 锁死页面在移动设备显示宽度
- 引入了 normalize.css, 在默认的HTML元素样式上提供了跨浏览器的高度一致性