## Dart选择html
要编写Dart Web应用程序，您需要了解几个主题 - DOM树，节点，元素，HTML以及Dart语言和库。

关于Dart，HTML和CSS


语言 | 功能
---|---
DART | 实现Web应用程序的交互性和动态行为
HTML | 描述Web应用程序页面的内容（文档中的元素和结构）
CSS | 管理页面元素的外观


Dart程序可以响应诸如鼠标点击之类的事件，动态地处理网页上的元素并保存信息。在部署Web应用程序之前，必须将Dart代码编译为JavaScript代码。

HTML是一种描述网页的语言。HTML使用标签设置初始页面结构，在页面上放置元素，并为页面交互嵌入任何脚本。HTML设置初始文档树并指定元素类型，类和ID，这些元素允许HTML，CSS和Dart程序引用相同的元素。

代表级联样式表的CSS描述了文档中元素的外观。CSS控制格式化的许多方面：输入面，字体大小，颜色，背景颜色，边框，边距和对齐等等。

### 关于DOM
文档对象模型（DOM）表示作为节点树的Web文档的结构。当HTML文件被加载到浏览器中时，浏览器解释HTML并在窗口中显示文档。下图显示了一个简单的HTML文件以及Chrome中生成的Web浏览器页面。

![image](https://webdev.dartlang.org/tutorials/images/simple-html.png)


HTML使用标签来描述文档。例如，上面的简单HTML代码使用页面标题的`<title>`标记，一级标题使用`<h1>`，段落使用`<p>`。HTML代码中的一些标签（如<head>和<body>）在网页上不可见，但确实对文档结构有所贡献。
在DOM中，文档对象位于树的根目录（它没有父项）。树中不同种类的节点表示文档中的不同种类的对象。例如，树具有页面元素，文本节点和属性节点。这是上面简单的HTML文件的DOM树。
![image](https://webdev.dartlang.org/tutorials/images/simple-dom-tree.png)

请注意，有些标记（如`<p>`段落标记）由多个节点表示。段落本身是一个元素节点。段落中的文本是文本节点（在某些情况下，可能是包含许多节点的子树）。而ID是一个属性节点。

除了根节点之外，树中的每个节点都只有一个父节点。每个节点可以有许多孩子。

一个HTML文件定义了文档的初始结构。Dart或JavaScript可以通过添加，删除和修改DOM树中的节点来动态修改该文档。当DOM改变时，浏览器立即重新渲染窗口。

![image](https://webdev.dartlang.org/tutorials/images/dynamic-dart.png)
该图显示了一个小型Dart程序，通过动态更改段落的文本来对DOM进行适度更改。程序可以添加和删除节点，甚至可以插入整个节点的子树。

### 创建一个新的Dart应用程序
1.进入DartPad。
2.点击New Pad按钮撤消上次访问DartPad时所做的任何更改。

`注意： 这些说明使用了DartPad，它隐藏了一些HTML样板代码。如果您想使用其他编辑器，那么我们建议您从一个小型Dart网络应用程序示例开始，并修改<body>部分中的非脚本标记。 HTML和Dart连接显示完整的HTML代码。`

### 编辑HTML源代码

1.点击HTML，在DartPad的左上角。该视图从Dart代码切换到（不存在的）HTML代码。
2.添加以下HTML代码：

```
<p id = “RipVanWinkle” >
RipVanWinkle.
</ p>
```

3.点击HTML OUTPUT查看浏览器如何呈现您的HTML。
### 编辑Dart源代码
1.点击DART，在DartPad的右上角。视图从HTML代码切换到Dart代码。

2.将Dart代码更改为以下内容：

```
导入'dart：html' ;

void main （）{
querySelector （'#RipVanWinkle' ）.text = 'Wake up, sleepy head!';
}

```
3.单击运行以执行您的代码。

### 关于HTML源代码

这个HTML代码类似于本教程前面各个图中的HTML代码，但它更简单。

在DartPad中，你只需要你真正关心的标签 - 在这种情况下，`<p>`。你不需要像<html>和<body>这样的标签。因为DartPad知道你的Dart代码在哪里，所以你不需要一个<script>标签。段落标签具有标识符“RipVanWinkle”。您在下一步创建的Dart代码使用此ID来获取段落元素。

### 编辑Dart源代码
1.点击DART，在DartPad的右上角。视图从HTML代码切换到Dart代码。

2.将Dart代码更改为以下内容：


```
import'dart：html' ;

void main （）{
querySelector （'#RipVanWinkle').text = 'Wake up, sleepy head!'; ; }
```
3.单击运行您的代码。

### 关于Dart源代码

import指令导入指定的库，使该库中的所有类和函数都可用于您的程序。


```
import 'dart:html'
```

该程序导入Dart的HTML库，其中包含用于编程DOM的关键类和函数。关键类包括：


Dart类 | 描述
---|---
node节点 | 实现一个DOM节点
元素 | Node的一个子类; 实现一个网页元素。
文件 | Node的另一个子类; 实现文档对象。


Dart核心库包含另一个有用的类:List，一个可以指定其成员类型的参数化类。元素的实例将其子元素的列表保存在List <Element>中。

### 使用querySelector（）函数

这个应用程序的main（）函数包含一行代码，它有点类似于一个接一个地发生多个事情的运行句子,让我们解构它。

querySelector（）是Dart HTML库提供的一个顶级函数，它从DOM中获取一个Element对象。


```
querySelector('#RipVanWinkle').text = 'Wake up, sleepy head!';
```
querySelector（）是一个字符串，它是一个标识对象的CSS选择器。最常见的CSS选择器指定类，标识符或属性。我们稍后会更详细地看这些，当我们添加一个CSS文件到迷你应用程序。在这种情况下，RipVanWinkle是HTML文件中声明的段落元素的唯一ID，并且#RipVanWinkle指定该ID。
```
querySelector('#RipVanWinkle').text = 'Wake up, sleepy head!';
```

从DOM获取元素的另一个有用的函数是querySelectorAll（），它通过元素列表返回多个Element对象 - 其中所有匹配提供的选择器。

### 设置元素的文本

在DOM中，页面元素的文本包含在子节点中，具体地说是文本节点。在下图中，包含字符串“RipVanWinkle段落”的节点是文本节点。
![image](https://webdev.dartlang.org/tutorials/images/paragraph-dom.png)

更复杂的文本（如带有样式更改的文本或嵌入的链接和图像）将用文本节点和其他对象的子树表示。

在Dart中，您可以简单地使用Element text属性，该属性具有一个getter，可以为您节点的子树，并提取文本。

```
querySelector('#RipVanWinkle').text = 'Wake up, sleepy head!';
```

但是，如果文本节点具有样式（因此是一个子树），获取文本然后立即设置它可能会更改DOM，作为丢失子树信息的结果。通常，与我们的RipVanWinkle示例一样，这种简化没有不利影响。

赋值运算符（=）将querySelector（）函数返回的Element的文本设置为字符串“Wake up，sleepy head！”。

```
querySelector('#RipVanWinkle').text = 'Wake up, sleepy head!';
```

这会使浏览器立即重新呈现包含此应用程序的浏览器页面，从而在浏览器页面上动态显示文本。

## Dart 添加HTML元素


### HTML和Dart连接
Dart网络应用程序在运行时动态改变浏览器窗口中的文本。当然，将文本放在浏览器页面上，而不用做其他事情，可以用直接的HTML来完成。这个小应用程序只显示如何从飞镖应用程序连接到浏览器页面。

在DartPad中，Dart代码和HTML代码之间唯一可见的连接是RipVanWinkle ID。

![image](https://webdev.dartlang.org/tutorials/images/dart-html-connect.png)

要在DartPad之外运行您的应用程序，您需要在HTML和Dart代码之间建立另一个连接：您必须将<script>标记添加到HTML以告诉浏览器在哪里查找Dart代码。您还必须添加其他HTML标记以提供浏览器所需的其他页面信息和结构。

这里是这个应用程序的完整HTML代码，假设Dart代码位于一个名为main.dart：


```
<!DOCTYPE html>

<html>
<head>
<title>A Minimalist App</title>
</head>

<body>
<p id="RipVanWinkle">
RipVanWinkle paragraph.
</p>

<script type="application/dart" src="main.dart"></script>
<script src="packages/browser/dart.js"></script>
</body>
</html>
```

这两个<script>标签是这个添加的HTML的唯一Dart特定部分。他们将Dart代码绑定到页面中，告诉浏览器在哪里找到Dart代码以及如何处理它。

下图总结了Dart和HTML代码之间的所有连接。

![image](https://webdev.dartlang.org/tutorials/images/dart-html-connect-full.png)

### 给应用程序一些CSS样式
大多数HTML使用级联样式表（CSS）来定义 控制页面元素外观的样式。让我们定制小应用程序的CSS。

1.点击CSS。视图从Dart代码切换到（不存在的）CSS代码。

2.添加以下CSS代码


```
#RipVanWinkle {
font-size: 20px;
font-family: 'Open Sans', sans-serif;
text-align: center;
margin-top: 20px;
background-color: SlateBlue;
color: Yellow;
}
```

HTML OUTPUT下的显示会立即更改以反映新的样式，这些样式仅适用于ID为RipVanWinkle的页面元素。

### 关于CSS选择器
ID，类和其他关于元素的信息在HTML中建立。您的Dart代码可以使用这些信息来使用CSS选择器来获取元素 - 一种用于在DOM中选择匹配元素的模式。CSS选择器允许CSS，HTML和Dart代码引用相同的对象。通常，选择器指定ID，HTML元素类型，类或属性。选择器也可以嵌套。

Dart程序中的CSS选择器非常重要，因为您可以在querySelector（）和querySelectorAll（）中使用它们来获取DOM中的匹配元素。Dart程序通常使用带有querySelector（）的ID选择器和带有querySelectorAll（）的类选择器。

以下是一些CSS选择器的例子：

选择器类型 | 例子 | 描述
---|---|---
ID选择器 | #RipVanWinkle| 匹配一个唯一的元素
HTML元素 | p| 匹配所有段落
HTML元素 | h1|匹配所有一级标题
类 |     .classname|将所有项目与类classname匹配
Asterisk|*|匹配所有元素
属性|input[type=”button”]|匹配所有按钮输入元素



`提示： 如您所见，即使没有CSS文件，迷你应用程序也会使用CSS选择器ID #RipVanWinkle。你不需要一个Dart程序的CSS文件。你也不需要一个CSS文件来使用CSS选择器。CSS选择器在HTML文件中建立，供Dart程序用来选择匹配的元素。`

我们来看看迷你应用程序的CSS代码。小应用程序的CSS文件有一个CSS规则。一个CSS规则有两个主要部分：一个选择器和一组声明。

![image](https://webdev.dartlang.org/tutorials/images/css-rule-explained.png)


在迷你应用程序中，选择器#RipVanWinkle是一个ID选择器，由散列标记（＃）指示; 它与指定的ID匹配一个唯一的元素，我们现在累了的RipVanWinkle段落元素。RipVanWinkle是HTML文件中的ID。它在CSS文件和Dart代码中使用散列标签（＃）引用。在HTML文件中没有句点（。）指定类名，并在CSS文件和Dart代码中用句点（。）引用。

CSS规则的大括号之间是一个声明列表，每个以分号（;）结尾。每个声明都指定一个属性及其值。这组声明一起定义了 所有匹配元素的样式表。样式表用于设置网页上匹配元素的外观。

![image](https://webdev.dartlang.org/tutorials/images/css-property-value.png)

RipVanWinkle段落的CSS规则指定了几个属性; 例如，它将文本颜色设置为黄色。



