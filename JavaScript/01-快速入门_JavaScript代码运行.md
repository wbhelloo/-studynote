
## 01 JavaScript代码运行

> 本教程摘自：[廖雪峰的博客 https://www.liaoxuefeng.com](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000)

- 方法1：

    第一种方法：`JavaScript`代码可以直接嵌在网页的任何地方，不过通常我们都把`JavaScript`代码放到 `<head>`

    > 由`<script>...</script>`包含的代码就是`JavaScript`代码，它将直接被浏览器执行。

- 方法2：

    第二种方法是把`JavaScript`代码放到一个单独的`.js`文件，然后在`HTML`中通过`<script src="..."></script>`引入这个文件：

    ```html
    <html>
    <head>
    <script src="/static/js/abc.js"></script>
    </head>
    <body>
    ...
    </body>
    </html>
    ```

## 02 JavaScript代码的调试

 - 打开 `Google Chrome` 浏览器

 - 点击 `F12`，即打开开发者工具，浏览器窗口就会一分为二。

 - 点击`Console`，在这个面板里可以直接输入`JavaScript`代码，按回车后执行。例如：

    ```javascript
    console.log('Hello');
    ```
