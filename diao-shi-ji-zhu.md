# 调试技术
##什么是调试
![调试](/assets/调试/调试.png)
调试（英语：Debugging / Debug），又称除错，是发现和减少计算机程序或电子仪器设备中程序错误的一个过程。
* 发现程序错误的存在
* 以隔离、消除的方式对错误进行定位
* 确定错误产生的原因
* 提出纠正错误的解决办法
* 对程序错误予以改正，重新测试

##调试Dart web app
Dart web 调试工具在本书中主要使用Chromium 浏览器的的扩张程序进行调试。调试的步骤如下所示。
- 首先打开Chromium浏览器中`更多工具`中的`扩展程序`

![扩展程序](/assets/调试/扩展程序.png)

- 然后打开开发者模式

![开发者模式](/assets/调试/开发者模式.png)

- 拖放安装

![拖放安装](/assets/调试/拖放安装.png)

![调试](/assets/调试/调试按钮.png)

## 如何定位错误
- Coding多了，你会有很好的直觉，那就首先跟着直觉走
- 折半查找

## 调试的基本步骤

### 1. 重现问题
##### 第一步： 重复所发生的问题
- “重现错误”是指找到一系列总是能导致错误出现的操作。
- 可能需要多次重现错误，因此要尽量避免任何多余的步骤
- 找到问题出在哪里
-- 通常，你的IDE会在console中显示出在哪一行出现了错误
- Identify steps to get to bug
-- Ex: start single player, room 2, jump to top platform, attack left,  …
-- Produce systematic way to reproduce

##### 第二步：使用断点暂停代码
- 用于暂停代码的工具称为断点
-- 你也可以断点成为计算机内部世界的“时间停止”
-- 在你的代码的世界里面，你可以扮演“上帝”

##### 第三步：单步调试代码
- 一步一步调试
对于可能出问题部分的代码一步一步调试。

### 2. 收集线索
- 收集线索
-- 那些因素可能导致这个问题
-- 例如: if crash using projectile, what about that code that handles projectile creation and shooting?
- And beware that some clues are false
-- 例如: if bug follows explosion may think they are related, but may be from something else
- Don’t spend too long - get in and observe
-- 例如: see reference pointer from arrow to unit that shot arrow should get experience points, but it is NULL
That’s the bug, but why is it NULL?

### 3. Pinpoint Error（定位错误）
- 提出假设，然后证明
-- 例如：suppose arrow pointer corrupted during flight.  Add code to print out values of arrow in air.  But equals same value that crashes.  Hypothesis is wrong.  But now have new clue.
- 分而治之的方法（注，也可以用上面的假设检验）。
-- Sherlock Holmes: “when you have eliminated the impossible, whatever remains, however improbably, must be the truth”
-- Setting breakpoints, look at all values, until discover bug
-- The “divide” part means break it into smaller sections
例如：if crash, put breakpoint ½ way.  Is it before or after?
-- Repeat.
-- Look for anomalies, NULL or NAN values

### 4. 修复问题
- 提出了解决方案。正确的解决方案取决于问题所在阶段。
-- 例如：late in code cannot change data structures.  Too many other parts use.
-- Worry about “ripple” effects.
- 理想情况下，需要原始编码器修复
-- If not possible, at least try to talk with original coder for insights.
- 考虑其他类似的情况，即使尚未报告。
-- 例如：Other projectiles may cause same problem as arrows did

### 5. 测试解决方法
- Obvious, but can be overlooked if programmer is sure they have fix (but programmer can be wrong!)
- So, test that solution repairs bug
-- Best by independent tester
- Test if other bugs introduced (beware “ripple” effect)


















