# Dart 编程初体验



首先引入一个及其简单的dart webapp。立即运行，其效果如图所示

![dart first app](http://xx)

该程序dart应用代码如下：
```dart
import 'dart:html';
void main() {
  querySelector('#sample_text_id')
    ..text = 'Click me!'
    ..onClick.listen(reverseText);
}

void reverseText(MouseEvent event) {
  var text = querySelector('#sample_text_id').text;
  var buffer = new StringBuffer();
  for (int i = text.length - 1; i >= 0; i--) {
    buffer.write(text[i]);
  }
  querySelector('#sample_text_id').text = buffer.toString();
}

```
其对应的html代码如下
```html
<!DOCTYPE html>

<html>
  <head>
    <meta charset="utf-8">
    <title>DartFirstApp</title>
    <link rel="stylesheet" href="index.css">
  </head>
  <body>
    <h1>DartFirstApp</h1>

    <p>Hello world from Dart!</p>
    <div id="sample_container_id">
      <p id="sample_text_id">Click me!</p>
    </div>
    <script type="application/dart" src="index.dart"></script>
    <script src="packages/browser/dart.js"></script>
  </body>
</html>

```
其对应的css代码如下
```css
body {
  background-color: #F8F8F8;
  font-family: 'Open Sans', sans-serif;
  font-size: 14px;
  font-weight: normal;
  line-height: 1.2em;
  margin: 15px;
}

h1, p {
  color: #333;
}

#sample_container_id {
  width: 100%;
  height: 400px;
  position: relative;
  border: 1px solid #ccc;
  background-color: #fff;
}

#sample_text_id {
  font-size: 24pt;
  text-align: center;
  margin-top: 140px;
  -webkit-user-select: none;
  user-select: none;
}


```

html和css大家都熟悉，本书不赘述。重点理解dart的编程模型。
- 程序结构

从程序结构出发，讲解大图
- 语言规范
引导学生掌握学习语言规范的能力。
