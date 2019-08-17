# 了解 npm install -S -D 的区别，看这篇就完事了

### 一、npm install -S -D 的区别

npm install module_name -S    即    npm install module_name --save    

**写入dependencies**



npm install module_name -D    即    npm install module_name --save-dev   

**写入devDependencies**



##### `npm install --save`

(1)会把`msbuild`包安装到`node_modules`目录中 
(2)会在`package.json`的`dependencies`属性下添加`msbuild` 
(3)之后运行`npm install`命令时，会自动安装`msbuild`到`node_modules`目录中 
(4)之后运行`npm install --production`或者注明`NODE_ENV`变量值为`production`时，会自动安装`msbuild`到`node_modules`目录中

##### `npm install --save-dev`

(1)会把`msbuild`包安装到`node_modules`目录中 
(2)会在`package.json`的`devDependencies`属性下添加`msbuild` 
(3)之后运行`npm install`命令时，会自动安装`msbuild`到`node_modules`目录中 
(4)之后运行`npm install --production`或者注明`NODE_ENV`变量值为`production`时，不会自动安装`msbuild`到`node_modules`目录中

其中 **install 可以简写为 i** ，即    npm i module_name -S



还有一个 npm i module_name -g ，-g 指的是**全局安装**。不带 -g 的为**本地安装**

##### `npm install`本地安装

（1）将安装包放在 `./node_modules` 下（运行 npm 命令时所在的目录），如果没有 `node_modules`目录，会在当前执行 `npm` 命令的目录下生成 `node_modules` 目录。 
（2）可以通过 `require()` 来引入本地安装的包。

##### `npm install -g`全局安装

(1) 将安装包放在 `/usr/local` 下或者你 `node` 的安装目录。 
(2)可以直接在命令行里使用。



### 二、dependencies 与 devDependencies 的区别

dependencies与devDependencies 都是在package.json中的配置信息。



![1618347-20190817163136187-1458311453](https://img2018.cnblogs.com/blog/1618347/201908/1618347-20190817163136187-1458311453.png)

- **devDependencies 里面的插件只用于开发环境，不用于生产环境**
- **dependencies 是需要发布到生产环境的。**



### **三、总结：**

**devDependencies** 的理解：

我们在开发一个前端项目的时候，需要使用到webpack或者gulp来构建我们的开发和本地运行环境，这时我们就要安装到devDependencies 里。webpack或者gulp是用来打包压缩代码的工具，在项目实际运行的时候用不到，所以把webpack或者gulp放到devDependencies 中就行了。

**dependencies** 的理解：

我们在项目中用到了element-ui或者mint-ui，在生产环境中运行项目，当然也需要element-ui或者mint-ui，所以我们把element-ui或者mint-ui安装到dependencies中。

