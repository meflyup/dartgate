# dart中的重要约定
每一种语言做开发都有一套约定，这些约定是为了开发者更好的组织代码、更好的交流。本质上，没有什么好说的。开始不熟悉的时候，多看看，看的多了，遵守的多了，自然熟烂于心了，就像红灯行、绿灯停一样。
>**本文档的内容主要来自[Pub Package Layout Conventions](https://www.dartlang.org/tools/pub/package-layout.html#public-directories),本文档阐述本课程关注的主要内容，其他内容请同学在需要的时候到原始文档自行查看。**  

## Pub Package Layout Conventions 
>下面的代码显示了一个比较完整的dart项目的目录结构约定。 

~~~dart
myDartApp
  .packages *
  pubspec.yaml
  pubspec.lock **
  README.md
  CHANGELOG.md
  LICENSE
  benchmark/
    make_lunch.dart
    packages/ ***
  bin/
    myDartApp
    packages/ ***
  doc/
    api/ ****
    getting_started.md
  example/
    lunch.dart
    packages/ ***
  lib/
    myDartApp.dart
    tortilla.dart
    guacamole.css
    src/
      beans.dart
      queso.dart
  packages/ ***
  test/
    myDartApp_test.dart
    tortilla_test.dart
    packages/ ***
  tool/
    generate_docs.dart
  web/
    index.html
    main.dart
    style.css
~~~  

>*自dart 1.12版本后，运行pub get会生成.packages文件，注意，不要将这个文件纳入到git等版本控制系统中。

>** pubspec.lock文件也是运行pub get后生成的，除非你的包是一个应用程序，否则也不要纳入到git等版本控制系统中。

>*** packages文件夹也是在pug
 get 命令后生成的，文件夹中的内容是链接到你执行pub get后从pub.dartlang.org下载出来的各种依赖包的本地文件系统。同样不要纳入版本控制系统中。

>****  doc/api 目录是你运行dartdoc命令后生成的文档和api参考目录，这些内容来自于你代码中的注释，因此也不需要放到版本控制系统中。

### 最基本的
~~~dart
myDartApp
  pubspec.yaml
  pubspec.lock 
    
~~~ 
每一个dart应用或者dart包都会包含着两个文件。首先是有pubspec.yaml，这个文件种最主要的是说明项目需要哪些包来支持开发，以及程序的入口。pub get，pub update等命令执行就是针对该文件，一旦运行了这命令之后，就会自动生成pubppec.lock文件，来锁定版本依赖。
###public 文件夹  
对其他包（包括应用程序）公开的文件夹有两个:一个是存放library 的lib文件夹，一个是存放一些运行脚本的bin目录。  
#### lib文件夹  

我们常常在代码中看到如下情况：
~~~ dart
import "package:test/test.dart";
void main(){
 //todo 
 test("test target classs functoin add", () {
    Target target=new Target();
    int expectVal=target.add();
    expect(expectVal, equals(7));
  });
}
~~~ 
其中import 就是导入第三方包总的lib文件目录中的各种需要的类和功能，比如上面的代码是导入test 包中的test.dart来支持测试开发。通过以下截图我们看到test 包的目录情况：
![screenshot-package-test](http).  
>注意 ，带有main()主函数的dart入口脚本程序是不能放到lib目录的。放进该目录后，如果使用import来引用，会出现无法解析目录地址的错误，也就是根本没法引用。带有main()主函数的dart入口脚本程序应该放到[entrypoint 目录中](https://www.dartlang.org/tools/pub/glossary.html#entrypoint-directory)



#### public tool 文件夹：bin
此目录存放可以公开的dart工具类脚本。如果你有一个包被其他的包依赖，那么你的包中的此目录中的dart脚本可以被其他包运行。一种方式是在你的public tool目录中直接使用pub run 运行，一种是在其他目录下使用pub global run。
>小测试：pub global run到底怎么运行，请尝试参考文档，自己动手来确定
如果你不希望你的一些dart 工具脚本被其他包使用，那么应该将他们都放到你包中的另一个独立文件夹 tool中。

