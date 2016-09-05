## web应用的结构简介
从传统到现代...
## 从服务器获取json数据，并动态添加到HTML中
接上一节课：本次课从网络获取数据，并动态添加到网页中。
从git clone 实例程序，[https://github.com/meflyup/dart-tutorials-samples.git](https://github.com/meflyup/dart-tutorials-samples.git),用webstorm打开其中的portmanteaux样例程序。
```
当分析这个程序的时候，尝试首先让同学根据前面的内容，回顾改程序的整体骨架结构。
让学生对该段程序产生熟悉感。然后具体到新的内容及httpRequest。当讲授httpRequest的时候，
引导学生查询[Dart API HttpResquest](https://api.dartlang.org/1.12.1/dart-html/HttpRequest-class.html)
```
```dart
// Copyright (c) 2012, the Dart project authors.  
// Please see the AUTHORS file for details. 
// All rights reserved. Use of this source code 
// is governed by a BSD-style license that can be 
// found in the LICENSE file.

import 'dart:html';
import 'dart:convert';

var wordList;

void main() {
  querySelector('#getWords').onClick.listen(makeRequest);
  wordList = querySelector('#wordList');
}

void makeRequest(Event e) {
  var path = 'https://www.dartlang.org/f/portmanteaux.json';
  var httpRequest = new HttpRequest();

  httpRequest
    ..open('GET', path)
    ..onLoadEnd.listen((e) => requestComplete(httpRequest))
    ..send('');
}

requestComplete(HttpRequest request) {
  if (request.status == 200) {
    List<String> portmanteaux = JSON.decode(request.responseText);
    for (int i = 0; i < portmanteaux.length; i++) {
      wordList.children.add(new LIElement()..text = portmanteaux[i]);
    }
  } else {
    wordList.children.add(new LIElement()
      ..text = 'Request failed, status=${request.status}');
  }
}

```