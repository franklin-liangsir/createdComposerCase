# createdComposerCase
创建一个composer项目的完整步骤，只阐述步骤指明总体框架，细枝末叶的问题自行百度！
## 准备工作
>1、准备windows电脑 (jd.com)
>2、安装PHP环境 (https://www.bt.cn/)
>3、安装composer (https://www.w3cschool.cn/composer/)
>4、安装git (https://www.w3cschool.cn/git/)
>5、准备GitHub账号一枚 (https://github.com)
>6、准备packagist账号一枚(http://packagist.p2hp.com/)

## 原理说明
>电脑(写代码的工具)-本地git(提交代码到GitHub的工具)-GitHub(装代码的容器)-packagist(统计展示GitHub中的项目)-composer(通过packagist的记录去中把GitHub中的代码拉下使用)

## 第一步：链接本地git和在线GitHub
>不连接，代码不能提交到GitHub，后面就瞎了，教程自己去百度。
>一般是ssh来打通git与GitHub

## 第二步：创建项目
>去GitHub可视化创建，填个名字就行，不需要做其他的操作。

## 第三步：clone项目
>执行git命令： git clone git@github.com:demo/demo.git
>注意如果您是用：git clone https://github.com/demo/demo.git，把项目删了用上面的方式。
>如果git@github.com弄不下来，检查第一步。

## 第四步：在通过powershell这个项目执行composer命令
>输入composer init 执行后，会一步一步出来东西。
>根据提示去百度每一步的意思，直到不提示了为止。

## 第五步：目录说明
>.git隐藏文件是版本管理包，自动生成的，自己百度怎么看到隐藏文件
>src您存放代码的核心文件，就是你的代码都写在这里面的。
>.gitignore,限制git不能提交哪些文件给github。
>composer.json,第四步自动生成的文件，里面的具体信息直接百度意思。
>composer.lock,这个文件一般通过.gitignore禁止提交。用户下载使用的时候自动生成，锁定版本。第一次用的老版本，某天新版本也会直接被更新下来了，程序就蹦了，直接锁定在老版本的意思。
>LICENSE 软件协议自动生成的，没啥用。
>README.md，使用文档。
```json
//特别注意：composer.json,autoload
//"Demo\\Demo\\": "src/"，意思是自动加载src中的各种文件。
//文件使用的命名空间为：
//namespace Demo/Demo
//use Demo/Demo
//当你用不起的时候，关注一下autoload
"autoload": {
    "psr-4": {
        "Demo\\Demo\\": "src/"
    }
},
```

## 第六步：在src中写你的代码
>coding...

## 第七步：提交代码
>git add .
>git commit -m "您的备注"
>git push -u origin master -f (全部舍弃线上的代码，本地的直接覆盖上去)

## 第八步：怎么弄版本1.0.0 2.0.0 3.0.0
>第七步只是提交到了master-dev上，如何提交1.0.0呢
>git tag (看看当前有哪些版本，有就不创建)
>git tag 1.0.0 (创建1.0.0)
>git tag (看看当前有哪些版本，看看创建成功了没)
>git push origin 1.0.0 (把版本提交到github，如果不提交1.0.0，就一直是老代码)
>注意：第一次至少要创建一个1.0.0。

## 第九步：怎么把GitHub代码弄到packagist上
>在git上拷贝：https://github.com/demo/demo.git
>packagist网站的栏目上看到提交点击进：复制https://github.com/demo/demo.git，提交。
>每次在git上提交了代码，要去packagist网站，找到你的项目更新一下才生效，有自动方法自己百度。

## 使用
>1、composer require demo/demo
>2、去composer.json->autoload->psr-4看看：Demo\\Demo\\,这个就是namespace Demo/Demo，use Demo/Demo
