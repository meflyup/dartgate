[**文档对象模型 \(**_**DOM**_**\)**](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model) 将 web 页连接到脚本或编程语言。通常这意味着 javascript, 但将 HTML、SVG 或 XML 文档建模为对象不是 javascript 语言的一部分。它给文档（结构树）提供了一个结构化的表述并且定义了一种方式—程序可以对结构树进行访问，以改变文档的结构，样式和内容。 DOM 提供了一种表述形式— 将文档作为一个结构化的节点组以及包含属性和方法的对象。从本质上说，它将 web 页面和脚本或编程语言连接起来了。

尽管通常会使用 JavaScript 来访问 DOM， 但它并不是 JavaScript 的一部分，它也可以被其他语言使用.

文档对象模型 \(DOM\) 是HTML和XML文档的编程接口。它提供了对文档的结构化的表述，并定义了一种方式可以使从程序中对该结构进行访问，从而改变文档的结构，样式和内容。DOM 将文档解析为一个由节点和对象（包含属性和方法的对象）组成的结构集合。简言之，它会将web页面和脚本或程序语言连接起来。

一个web页面是一个文档。这个文档可以在浏览器窗口或作为HTML源码显示出来。但上述两个情况中都是同一份文档。文档对象模型（DOM）提供了对同一份文档的另一种表现，存储和操作的方式。 DOM是web页面的完全的面向对象表述，它能够使用如 JavaScript等脚本语言进行修改。

[W3C DOM](http://www.w3.org/DOM/) 和[WHATWG DOM](https://dom.spec.whatwg.org/)标准在绝大多数现代浏览器中都有对DOM的基本实现。许多浏览器提供了对W3C标准的扩展，所以在使用时必须注意，文档可能会在多种浏览器上使用不同的DOM来访问。

例如，W3C DOM 中指定下面代码中的`getElementsByTagName方法必须要返回所有<P>` 元素的列表：

```js
paragraphs = document.getElementsByTagName("P");
// paragraphs[0] is the first <p> element
// paragraphs[1] is the second <p> element, etc.
alert(paragraphs[0].nodeName);
```

参考

[https://developer.mozilla.org/zh-CN/docs/Web/API/Document\_Object\_Model/Introduction](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model/Introduction)

[https://developer.mozilla.org/zh-CN/docs/Web/API/Document\_Object\_Model](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model)

