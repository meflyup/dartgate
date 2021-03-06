# [**文档对象模型 \(**_**DOM**_**\)**](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model)

将 web 页连接到脚本或编程语言。通常这意味着 javascript, 但将 HTML、SVG 或 XML 文档建模为对象不是 javascript 语言的一部分。它给文档（结构树）提供了一个结构化的表述并且定义了一种方式—程序可以对结构树进行访问，以改变文档的结构，样式和内容。 DOM 提供了一种表述形式— 将文档作为一个结构化的节点组以及包含属性和方法的对象。从本质上说，它将 web 页面和脚本或编程语言连接起来了。

## DOM 和 JavaScript {#DOM_and_JavaScript}

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

有操作和创建web页面的属性，方法和事件都会被组织成对象的形式（例如，

`document`

对象表示文档本身，

`table`

对象实现了特定的

`HTMLTableElement`

DOM 接口来访问HTML 表格等）。本文会介绍基于 Gecko浏览器的 DOM 面向对象引用。

DOM 被设计成与特定编程语言相独立，使文档的结构化表述可以通过单一，一致的API获得。尽管我们在本参考文档中会专注于使用JavaScript， 但DOM 也可以使用其他的语言来实现， 以Python为例，代码如下：

```py
# Python DOM example
import xml.dom.minidom as m
doc = m.parse("C:\\Projects\\Py\\chap1.xml");
doc.nodeName # DOM property of document object;
p_list = doc.getElementsByTagName("para");
```

## Dart 和html的关系 {#How_Do_I_Access_the_DOM.3F}

|  |
| :--- |


| Language | Purpose |
| :--- | :--- |
| Dart | 实现对web应用的动态行为的交互控制 |
| HTML | 描绘页面内容、结构 |
| CSS | 给页面定义不同的外观 |

## Dart如何访问 DOM? {#How_Do_I_Access_the_DOM.3F}

DOM的样子如图所示

![](/assets/html&DOM.png)

![](/assets/domtree.png)

在使用DOM时，您不需要做任何其他特殊的操作。不同的浏览器都有对DOM不同的实现， 这些实现对当前的DOM标准而言，都会呈现出不同程度的一致性，每个web浏览器都会使用一些文档对象模型，从而使页面可以被脚本语言访问。

![](/assets/querySelector.png)

```dart
var domElement=querSelector("#RipVanWinkle")//这里是使用elementID来选择DOM元素的
```

参考

[https://developer.mozilla.org/zh-CN/docs/Web/API/Document\_Object\_Model/Introduction](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model/Introduction)

[https://developer.mozilla.org/zh-CN/docs/Web/API/Document\_Object\_Model](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model)

