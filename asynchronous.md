# Dart中的异步技术
异步技术在现代web编程中占有举足轻重的技术。受传统编程思维的惯性影响，初学者对于异步技术难以理解和把控。因此，这一节主要通过对比和简单案例来阐释什么事异步技术，为何要异步技术。同学基本理解后，通过亲自编写代码，查看文档深入理解和掌握。
##生活中的异步特性  
你有没有碰到生活中做事情，必须一环套一环的做。前面的事情没完成，后面的只能等着？比如你要买车票，必须先去取钱，没有取到钱，你是无论如何买不了票。你的事情必须一个接一个的来处理。在编程中，这种特性成为**同步**。  
那什么是**异步**呢？假设你现在在一个很熟悉的老板那里买东西，身上忘了带钱，为了不当误你买东西继续做其他的事情，你跟老板说：今天忘带钱了，我先赊着，明天有钱了送给你吧。老板爽快的说：行。明天记得带来。你开开心心的把东西拿走。同时，为了避免日后纠纷，你在老板出留了个欠条。你该拿着这个东西干嘛就干嘛去。第二天，你有钱了，就到老板那里把钱还了，把欠条收回。这种不影响你继续做当前的事情，而将其中一件事情放到日后当你完成了某件事情（也就是有钱了）后回来处理的机制就是*异步*。  
显然，生活中的这种*异步*机制有时候会很方便。不是吗？你还能想到什么生活中的*异步*现象吗？打电话是不是？
##web编程中为何要用异步机制  
回想十年前，大家用网页的时候，有没有碰到网页点一下链接，就必须等一下，等到那个页面完全载入才能继续点另一个链接？这种用户体验放到现在的话，网站肯定没多少人光顾。这就是web app中的*同步*机制的弊端。而现代很多web app中，你经常可以不停的点击各种按钮、链接，页面从不停止对你的响应。这就是web app中的*同步*制带来流畅的用户体验。这就是web 编程中*异步*的好处。  
## dart如何实现异步  
Dart的异步编程的特点是Future和Stream类。Future代表的是一个不能立即完成的计算。当一个正常函数返回结果时，异步函数返回一个Future，它最终将包含结果。Future会告诉你什么时候结果已经准备好了。
一个Stream是一个异步事件的序列。它就像一个异步的迭代，当你请求它时，它并没有得到下一个事件，而是告诉你它已经准备好了。

大概理解了*同步*和*异步*的概念后。让我们来接触dart语言中的异步机制。

<!--
```dart
// 用连续async 和await顺序执行，确保后面的语句在前面的语句执行后才执行
```
main() async {
  await expensiveA();
  await expensiveB();
  doSomethingWith(await expensiveC());
}  
//只有expensiveA（）执行结束后，expensivB()才执行。
```
-->

###dart异步程序的比喻
设想我们同学排成一列在食堂窗口打饭。每一位同学代表程序中的一条语句。很显然，同学打饭必须一个接着一个的来，前面一个同学没有打完饭，后面的只能等着。这是我们前文介绍过的*同步*现象。为方便理解和叙述，我们假设有10位同学，每一位同学打饭费时1分种，全部10位同学打好饭需要10分钟。现在，假设处在第3位同学位置，时间在第2分钟。可是这位同学发现发现卡没有钱了，于是他让一个同学帮他到楼下充值点充值，这位同学不想辛苦排队就此浪费，于是站在旁边让第4位同学继续。那位同学充值来回需要2分钟。在这连分钟内排第5位同学已经打好饭了。当那位同学回来时，这位同学可以继续打饭了。Ta有本来的第3位打饭变成现在第5为打饭了。  
在dart中有两种方式来做异步编程，一种是直接用底层Future API来做；一种是利用async 和await来简化开发。async和await简化了dart异步程序开发过程。开发人员用**同步**的习惯来写**异步**程序，整个语句看上去就跟同步程序风格相似。使用async和await可以免除调用Future API的繁琐。
关于此技术的原始文档请在[dart Future](https://www.dartlang.org/docs/tutorials/futures/)查看。  
我们将这段话转换为dart语言程序。  

```dart
import "dart:async";

main() {
  stu1();
  stu2();
  stu3();
  stu4();
  stu5();
  stu6();
  stu7();
  stu8();
  stu9();
  stu10();
}

void stu1() => print("stu1 done");

void stu2() => print("stu2 done");

void stu4() => print("stu4 done");

void stu5() => print("stu5 done");

void stu7() => print("stu7 done");

void stu8() => print("stu8 done");

void stu9() => print("stu9 done");

void stu10() => print("stu10 done");


Future stu3() async{
  int aNum = await stu3_recharge();
  print("stu3 done,recharge:" + aNum.toString());
}

Future stu6() async{
  int aDouble = await stu6_recharge();
  print("stu6 done,recharge:"+ aDouble.toString());
}

Future<int> stu3_recharge() async {
  int aNum;
  for (int i = 0;i < 10000000;i++) {
    aNum = i;
  }

  return aNum;
}

int stu6_recharge() {
  int balance;
  for (int i = 0;i < 10000;i++) {
    balance = i;
  }
  return balance;
}

```  
```
运行结果
stu1 done
stu2 done
stu4 done
stu5 done
stu7 done
stu8 done
stu9 done
stu10 done
stu6 done,recharge:9999
stu3 done,recharge:9999999
```
请思考  
>async 和await的作用域？ 

###异步中的同步
在上次课中，很多同学遇到了明明从数据库中读出来数据，在console中都打出来了。但是浏览器返回的确不是。这个问题的根源在异步读取数据库记录返回结果的时间比服务器响应用户的request的时间长。因此，在还没有来得及准备好数据的时候，服务器已经响应了客户端的http request。怎么办？在答疑中有些同学问过这个问题，我建议大家阅读dart中关于async的文档，找到调和二者的方法。 如何调和？  
- 时间是关键
- 很自然的想法：等从数据库成功取回数据后，在响应给客户端
- 因此，这是不是又回到了同步编程的模式！

调和方法确实存在。大家可在[Future Guide](https://www.dartlang.org/docs/tutorials/futures/)页面中尝试找解决方案。  

