- 是的，最终程序可以在所有浏览器上运行，甚至开发阶段也可以。dart只能在开发版的chromtrium（就是你们配置中的那个程序）中直接运行，在其他的浏览器中运行的时候，dart 内部的机制(dart2js)会把它翻译转化成javascript，从而能跨多种浏览器运行。
eg:
>dart2js main.dart
>ls
main.dart
main.js