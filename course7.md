# 使用github提交作业
如果你在上节课中成功添加自己到organization：ECNU-DEIT-2013中，那么请继续如下操作。
1. 打开github desktop软件。用各自的github网站注册的账号密码登录。如图所示。


![登陆github desktop-1](http://img1.ph.126.net/Pn1Lt15bFvv9Z86StwHVDQ==/6630214544677387705.jpg)

![登陆github desktop-2](http://img0.ph.126.net/_ZOCQzxr4n-wkJsrqt8GvA==/6631386624072019065.jpg)

这个项目是每位同学独立完成的平日dart编程练习，每个人对应一个分支，分支描述为 your_studentID。其中x是练习的序号，每次累加。

1. clone exercise项目到本地

  ![clone 项目](http://img0.ph.126.net/ULoW987fckSLqdTbSxP2wA==/6630811579491955638.jpg)
2. 创建你的分支（branch）以your_studentID命名。如图所示

  ![screenshot-new-branch](http://img2.ph.126.net/CNifnmleZNfg6KVUxhuViw==/6630240932956451438.png)
3. 使用webstorm打开clone下来的项目
  - 打开pubspec.yaml文件
  - enable dart suport
    ![enable dart support](http://img0.ph.126.net/aXqb_uceuAO0vzrTC5tStg==/6630695031259275024.png "enable dart support")
  - 点击get denpendence 按钮
    ![get denpendece](http://img0.ph.126.net/x83fNB_bZAno7GaZYu05Qw==/6630710424421903305.png 'get dependencies')
 - 运行一下，看是否正常运行。
 ![run index](http://img0.ph.126.net/W0cKBGjKheipC3r8tj2_AQ==/6631365733350874332.png 'run ')
4. 如平常一样编程，编程修改各自的dart文件和html文件
5. **由于各自使用了自己喜爱的昵称，我不知道大家是谁。想来想去使用这个方法吧：请用你的学号作为  branch（注意从master创建branch，不要从别的同学的branch创建）。且以后每次作业不必再创建新的branch了，而是作为一个新的commit提交。commit名称用exercise_x,其中x表示 1，2，...以此类推。但是不是作为最终提交的commit命名不要用exercise-x
6. ** 
![id-name](http://img2.ph.126.net/ymg68brO1fuF3IuWF_rqFw==/6630327794374964546.png)
提交新作业，如图：
![commit_exercise_x](http://img0.ph.126.net/-tkDUtT4kyXHegVQoGq_bQ==/6630529005002847564.png)
提交后，别忘了右上角的publish（或者sync），如图：
![publish_exercise_x](http://img0.ph.126.net/kFpNW891Gsq3iZUVzievGg==/6631307459234648688.png)

5. 提交修改的文件
6. 老师可能会在代码中留批注，请用github desktop软件 同步你的代码看最新内容，或者在github网站中看批注内容，效果如图所示
7. ![screenshot-exercise-comment](http://img2.ph.126.net/6OtoW6GGKInud36ZHZKGqw==/6631321752886057121.jpg)
------------
~~#作业
鉴于本次国庆放假，损失了几节课，望课外大家抓紧：
1. 在上次的add程序基础上写一个从1加到100的程序。
2. 各小组抓紧各自项目的设计，特别是技术分解，把设计的ppt，技术分解思路提交到各小组的有道群中。上次不合适的小组也请加紧选题加紧设计
3. **课堂没太跟上的，环境总有问题的，请充分利用课外时间，我可协助，课堂没有时间解决这种耗时间的环境问题**~~

#github提交作业的推荐流程
为避免出现修改提交冲突，请谨遵如下推荐工作流程：
{% mermaid %}
graph TD;
  使用github同步-->在webstorm中打开修改;
  在webstorm中打开修改-->在github中查看change;
  在github中查看change-->提交;
  提交-->使用github同步;
{% endmermaid %}

- tips:

 >什么情况下回出现冲突:比如老师查看了各位同学的作业，老师在其中一段代码处多了修改，并且commit也同步到网上了，那么同学如果没有同步下来，依然上次提交的代码（也就是老师批改前的代码）来做新的工作，那么很可能你和老师修改了同一处，这就会出现冲突；一旦出现冲突你就不能顺利commit，就必须人为干预。
