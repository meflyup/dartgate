## Dart中的html事件处理

### 什么是事件
事件是文档或浏览器窗口中发生的一些特定的交互瞬间，我们使用监听器（listener/hanlder）来预订事件，当事件触发时，执行相对应的代码，这种就是传统软件工程中被成为观察者模式的模型，这种模型支持页面的行为与页面的UI之间的松散耦合。如JavaScript与HTML之间通过事件来进行交互。
### 事件流
当一个HTML元素产生一个事件时，该事件会在元素节点与根结点之间的路径传播，路径所经过的结点都会收到该事件，这个传播过程可称为DOM事件流。 而事件流有两种：
- 事件冒泡
- 事件捕获

#### 事件冒泡

IE的事件流叫做事件冒泡（event bubbling），即事件开始时由最具体的元素（文档中嵌套层次最深的那个节点）接收，然后逐级向上传播到较为不具体的节点。 如HTML文档：

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
</head>
<body>
<div> click </div>

</body>
</html>
```

当我们点击页面中的div元素时，这个click事件会按照如下的顺序传播：
![image](https://github.com/meflyup/dartgate/raw/master/assets/%E4%BA%8B%E4%BB%B6%E5%86%92%E6%B3%A1.jpg)

#### 事件捕获

事件捕获的思想是不太具体的节点应该更早接收到事件，而最具体的节点应该最后接收到事件。事件捕获的用意在于在事件到达预定目标之前捕获它。如HTML代码：



```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
</head>
<body>
<div> click </div>

</body>
</html>
```

当单击元素就会以下列顺序触发 click 事件：

![image](https://github.com/meflyup/dartgate/raw/master/assets/%E4%BA%8B%E4%BB%B6%E6%8D%95%E8%8E%B7.jpg)

#### 事件对象Event
对象代表事件的状态，比如事件在其中发生的元素、键盘按键的状态、鼠标的位置、鼠标按钮的状态。事件通常与函数结合使用，函数不会在事件发生前被执行。在触发 DOM 上的某个事件时，会产生一个事件对象event，这个对象中包含着所有与事件有关的信息。包括导致事件的元素、事件的类型以及其他与特定事件相关的信息。例如，鼠标操作导致的事件对象中，会包含鼠标位置的信息，而键盘操作导致的事件对象中，会包含与按下的键有关的信息。所有浏览器都支持event对象，但支持方式不同。
### HTML 事件处理

某个元素支持的每种事件，都可以使用一个与相应事件处理程序同名的 HTML 特性来指定。如下面代码中，事件e 将元素id=idname元素的值设置成文本输入字段的值。


```
void updateBadge(Event e) {
querySelector('#idname').text = e.target.value;
}

```

