## 事件机制
### 首先看一个示例



```
// Copyright (c) 2012, the Dart project authors.  Please see the AUTHORS file
// for details. All rights reserved. Use of this source code is governed by a
// BSD-style license that can be found in the COPYING file.

// This is a port of "Native HTML5 Drag and Drop" to Dart.
// See: http://www.html5rocks.com/en/tutorials/dnd/basics/


import 'dart:html';

class Basics {
///这一行是做什么的？
Element _dragSourceEl;
/// 这个函数是做什么？
void start() {
///这个是新的selector，做什么？
var cols = document.querySelectorAll('#columns .column');
for (var col in cols) {
col.onDragStart.listen(_onDragStart);
col.onDragEnd.listen(_onDragEnd);
col.onDragEnter.listen(_onDragEnter);
col.onDragOver.listen(_onDragOver);
col.onDragLeave.listen(_onDragLeave);
col.onDrop.listen(_onDrop);
}
}
///这个function做什么？
void _onDragStart(MouseEvent event) {
///event.target是什么？
Element dragTarget = event.target;
///这个是做什么的？
dragTarget.classes.add('moving');
_dragSourceEl = dragTarget;
event.dataTransfer.effectAllowed = 'move';
///这个是做什么的？
event.dataTransfer.setData('text/html', dragTarget.innerHtml);
}
///这个function做什么？
void _onDragEnd(MouseEvent event) {
Element dragTarget = event.target;
dragTarget.classes.remove('moving');
var cols = document.querySelectorAll('#columns .column');
for (var col in cols) {
col.classes.remove('over');
}
}
///这个function 做什么？
void _onDragEnter(MouseEvent event) {
Element dropTarget = event.target;
dropTarget.classes.add('over');
}
///这个function 做什么？
void _onDragOver(MouseEvent event) {
// This is necessary to allow us to drop.
event.preventDefault();
event.dataTransfer.dropEffect = 'move';
}
///这个function 做什么？
void _onDragLeave(MouseEvent event) {
Element dropTarget = event.target;
dropTarget.classes.remove('over');
}
///这个function 做什么？
void _onDrop(MouseEvent event) {
// Stop the browser from redirecting.
///去掉这个试试看？
event.stopPropagation();

// Don't do anything if dropping onto the same column we're dragging.
Element dropTarget = event.target;
if (_dragSourceEl != dropTarget) {
////这里做什么？
_dragSourceEl.innerHtml = dropTarget.innerHtml;
dropTarget.innerHtml = event.dataTransfer.getData('text/html');
}
}
}

void main() {
var basics = new Basics();
basics.start();
}
```


如果你已经clone了eduapp，那么请切换到master分支上：
```
git checkout master
git pull
```
之后在vscode中打开这个项目。你可以用
```
pub serve
```

运行起来，效果如图：

![image](https://github.com/meflyup/dartgate/raw/master/assets/dnd.png)

### 代码分析

事件驱动的编程有三个主要的概念，他们分别是事件源，事件本身以及事件的处理，最后还有一个是事件队列。在本例子中。

#### 事件源


```
var cols = document.querySelectorAll('#columns .column');
for (var col in cols) {
col.onDragStart.listen(_onDragStart);
col.onDragEnd.listen(_onDragEnd);
col.onDragEnter.listen(_onDragEnter);
col.onDragOver.listen(_onDragOver);
col.onDragLeave.listen(_onDragLeave);
col.onDrop.listen(_onDrop);
}
```

每一个col都是一个事件源，他们被用户操作后，将把事件传播出去。在这个例子中，他们传播的是DragStart，DragEnd，DragOver，DragLeave和Drop。

#### 事件本身
事件本身是对事件信息的封装，比如本例子中，event就代表着事件，我们可以使用event来查看里面的各种信息，如图所示，我们通过调试（随后的课程会学习调试）可以看到event所包含的各种信息，比如这个事件是从哪个事件源来的，如果是鼠标操作，是那些button，鼠标的位置坐标，是否同时按住了键盘功能键等等。

```
void _onDragStart(MouseEvent event) {
///event.target是什么？
Element dragTarget = event.target;
///这个是做什么的？
dragTarget.classes.add('moving');
_dragSourceEl = dragTarget;
event.dataTransfer.effectAllowed = 'move';
///这个是做什么的？
event.dataTransfer.setData('text/html', dragTarget.innerHtml);
}

```
![image](https://github.com/meflyup/dartgate/raw/master/assets/event.png)


#### 事件handle



```
void _onDragEnd(MouseEvent event) {
Element dragTarget = event.target;
dragTarget.classes.remove('moving');
var cols = document.querySelectorAll('#columns .column');
for (var col in cols) {
col.classes.remove('over');
}
}
```
一个事件从触发（trigger）到被处理，需要为这个事件赋予一个handle。在dart中，这些handle都可以用上述代码形式来定义。它本质上就是一个function，其返回类型是 void，名称可以自定义，参数列表中至少包括一项 xxxEvent 也就是特定类型的事件。比如你可以定义鼠标点击事件：


```
void onClick(MouseEvent e){
//参数列表e和event是等价的，这是参数名，你也可以自定义试试看
//添加各种处理该事件的代码
}
```

####  注册这个事件handle
最后，需要为这个事件注册这个handle。注册handle通常就是用如下形式：

```
col.onDragStart.listen(_onDragStart);
```

- col是事件源
- onDragStart就是该事件源会出发的一个事件，有很多其他的事件，可以参考 W3C标准文档 UIEvents。
- .listen()function参数填写的就是handle的function名字
![image](https://github.com/meflyup/dartgate/raw/master/assets/registerHandle2.png)

### 事件驱动的编程模式

通常可以分为事件驱动的编程模式（Event-driven programming）和批处理模式（batch programming）

基本上我们所接触的应用都是事件驱动的编程模式做出来的应用，操作系统，word，网页...；一下是一章批处理编程的代码样子。

![image](https://github.com/meflyup/dartgate/raw/master/assets/batchprogramming.png)


我们可以这样理解二者的关键区别

- 批处理像是决定论，一开始所有的运作都有程序员固定了，程序员就是这个代码的 *上帝 * 。而事件驱动的应用是没有固定运行路径的，只要不死机，他可变动的路径依据软件所提供的功能来说可能是无穷的，他是因事件而改变的。

- 再从我们人自身的情况来理解。我们每个人自生命形成之时就无时无刻的通过至少五感：
- 眼
- 耳
- 鼻
- 舌
- 身

来感知这个世界。我们无时无刻不作出某种决策以响应所接受到的外部世界的事件触发。比如我点名，这是一个onHear事件；每个同学事实上在大脑中都注册了一个接受点名的handle，这个handle里面首先做的事情是判断是否由点到自己的名字，如果不是自己的名字，就可以万事大吉了：），如果是自己的名字，就开始思考怎么回答老师的问题。我们的大脑代码就像

```
brain.onHear.listen(_onHearHandle);
void _onHearHandle(EarEvent e){
if(e.name==myname){
//todo
}else{
//嘿嘿...不是我。
}
}
```

