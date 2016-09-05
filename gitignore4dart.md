# gitignore4dart

与IDE相关的各类xml配置文件，以及编译的中间文件通常不需要用git管理，因此请在项目根目录配置，.gitignore文件来描述不需要git管理的文件类型。对于使用webstorm来开发dart web app，.gitignore文件内容如下：
```
# Don’t commit the following directories created by pub.
.buildlog
.pub/
build/
packages
*.idea
# Or the files created by dart2js.
*.dart.js
*.js_
*.js.deps
*.js.map
# Include when developing application packages.
pubspec.lock

```
在webstorm中，如图：
![gitignore](http://img1.ph.126.net/_ASPuUpoYI2DgceanMuATA==/6630593876189535955.png)

我初始化的项目中有这个文件，如果clone后因为各种原因没有发现这个文件，请自己创建一个，如图所示：
![gitignore-create-1](http://img0.ph.126.net/90IIXtWJOTPRG5CB38GPCA==/6631429505025328446.png)
![gitignore-create-2](http://img2.ph.126.net/02TIqjP4JkYhVvjSGl9G4g==/6631429505025328442.png)
然后修改内容为上面的内容即可。创建这个文件后，github中只会显示dart，html和css等少数文件的修改状态，那样就对了，如果还是现实各种.xml 乱七八糟的东西，那就说明没有配置好，请仔细检查，或者寻求帮助。