# 前端开发代码规范

@(规范)[代码]

**开发规范** ：包括开发、部署的目录规范，编码规范等。不要小瞧规范的威力，可以极大的提升开发效率，真正优秀的规范不会让使用者感到约束，而是能帮助他们快速定位问题，提升效率。：
 
- **代码规范** ：前端开发代码书写习惯；
- **参考** ：[alloyteam](http://alloyteam.github.io/CodeGuide/#project-naming)；

-------------------

[TOC]

## 命名规则

### 项目命名
- 全部采用小写方式， 以下划线分隔。
``` shell
eg：wp_pjs_pc
```

### 目录命名
- 使用驼峰命名规则；有复数结构时，要采用复数命名法。
``` shell
eg：scripts, styles, images, dataModels, dataServices
```

### JS文件命名
- 使用驼峰命名规则
``` shell
eg：accountModel.js
```

###  CSS, SCSS文件命名
自动化构建工具
- 参照JS文件命名，使用驼峰命名；
``` shell
eg：wpSprites.scss
```

###  HTML文件命名
自动化构建工具
- 参照项目命名规则，使用驼峰命名；
``` shell
eg：errorReport.html
```


## HTML
```html
<!DOCTYPE html>
<html xmlns:ng="http://angularjs.org" lang="en">
<head>
	<meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
	<meta http-equiv="pragma" content="no-cache"/>
	<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
	<title></title>
	<meta name="keywords" content="" />
	<meta name="description" content="">
	<!-- css加载 -->
</head>
<body></body>
<!-- js加载 -->

</html>
```
### 语法
- 缩进使用soft tab（4个空格）；
- 嵌套的节点应该缩进；
- 在属性上，使用双引号，不要使用单引号；
- 属性名全小写，用中划线做分隔符；
- 不要在自动闭合标签结尾处使用斜线（HTML5 规范 指出他们是可选的）；
- 不要忽略可选的关闭标签

###HTML5 doctype
在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；虽然doctype不区分大小写，但是按照惯例，doctype大写 ；

###  lang属性
根据HTML5规范：
> 应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。

###  字符编码
通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'UTF-8'。

###  IE兼容模式
用 <meta> 标签可以指定页面应该用什么版本的IE来渲染；

###  引入CSS, JS
根据HTML5规范, 通常在引入CSS和JS时不需要指明 type，因为 text/css 和 text/javascript 分别是他们的默认值。建议加上type类型
- css文件在head头部加入
- js文件加在body后

###  属性顺序
属性应该按照特定的顺序出现以保证易读性；
- class
- id
- name
- data-*
- src, for, type, href, value , max-length, max, min, pattern
- placeholder, title, alt
- aria-*, role
- required, readonly, disabled

>class是为高可复用组件设计的，所以应处在第一位；
 id更加具体且应该尽量少使用，所以将它放在第二位。

###  boolean属性
boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要；
```html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
<select>
    <option value="1" selected>1</option>
</select>
```
> boolean属性的存在表示取值为true，不存在则表示取值为false。


## CSS, SCSS (参照[alloyteam](http://alloyteam.github.io/CodeGuide/#project-naming))


## JavaScript (参照[alloyteam](http://alloyteam.github.io/CodeGuide/#project-naming))
### 变量命名
- 标准变量采用驼峰式命名
- 'ID'在变量名中全大写
- 'URL'在变量名中全大写
- 'Android'在变量名中大写第一个字母
- 'iOS'在变量名中小写第一个，大写后两个字母
- 常量全大写，用下划线连接
- 构造函数，大写第一个字母
- jquery对象必须以'$'开头命名
```javascript
var thisIsMyName;
var goodID;
var reportURL;
var AndroidVersion;
var iOSVersion;
var MAX_COUNT = 10;
function Person(name) {
    this.name = name;
}
// not good
var body = $('body');
// good
var $body = $('body');
```

### 文档注释
```javascript
/**
 * @func
 * @desc 一个带参数的函数
 * @param {string} a - 参数a
 * @param {number} b=1 - 参数b默认值为1
 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
 * @param {object} d - 参数d为一个对象
 * @param {string} d.e - 参数d的e属性
 * @param {string} d.f - 参数d的f属性
 * @returns {boolean} 返回值为true
 */
function foo(a, b, c, d) {
    ...
}
```

> [参考](http://yuri4ever.github.io/jsdoc/#@returns)

##性能优化原则及分类
| 优化方向      |    优化手段|
| :-------- | :--------|
| 请求数量  | 合并脚本和样式表，CSS Sprites，拆分初始化负载，划分主域
| 请求带宽     |   开启GZip，精简JavaScript，移除重复脚本，图像优化
| 缓存利用      |    使用CDN，使用外部JavaScript和CSS，添加Expires头，减少DNS查找，配置ETag，使AjaX可缓存
| 页面结构	|将样式表放在顶部，将脚本放在底部，尽早刷新文档的输出


### Git规范
#### 分支
```shell
    1、master 分支为主分支(保护分支)，不能直接在master上进行修改代码和提交；master分支对应线上版本。

    2、dev 分支为测试分支，所以开发完成需要提交测试的功能合并到该分支；dev分支对应开发版本。

    3、master、release、dev 分支只能由开发组长合并及提交，其余人员需要在各自分支上进行开发工作。

    4、task/bug 分支为开发分支，大家根据tapd 不同的任务 ID 创建独立的功能分支，开发完成后合并到dev分支。

    5、git提交尽量遵循单次提交的代码是对一个完整但是影响尽量小的功能的修改，不要把对几个功能的修改混在一起提交。

    6、注释最少应该写清楚本次做的修改和达到的效果，越详细越好（最好是任务名称 + 任务说明）。

    7、分支一定要从 master 的最新 tag 拉出（除非有特殊要求），分支名字必须有明确的含义，以方便管理。

    8、功能上线后，对应的分支应该及时删除。

    9、分支名字的命名方法为：task 或 bug 开头，加 tapd 任务ID，示例：task/ID1018393 。

    10、没有 tapd task/bug ID 的，请找相关人员去创建 task 或 bug，特殊的使用特殊分支，示例：bug/999999 。

    11、不要直接往 release 提交功能代码，release 代码更新来源应该是 dev 。
    
    12、不要直接往 dev 提交功能代码，dev 代码更新来源应该是其他分支。

    13、分支不能重复使用，分支与分支之间不能相互合并（多人开发同一模块，需要共享代码时，拉出来的功能性主分支除外）。

    14、同一个任务多次提交时尽量使用 rebase 合并 commit ，减少push次数，方便查看提交记录。
```

#### 提交commit信息
```shell
    1、git commit 注释信息的第一行必须以小写 task/bug ，加tapd 上对应的 task/bug 号（也就是分支名开头），后面写详细内容。

    2、请避免不写注释直接提交。

    3、示例：task/ID1018393 【app】【模块】【子模块】详细内容... 。
```

#### 注意
```shell
    请先配置本地 git 信息
    
    $ git config --global user.name "张三"
    $ git config --global user.email "eamil@qq.com"
        
    name 一定是开发者的中文姓名，方便查看和管理。
```

## 编辑器配置和构建检查 (参照[alloyteam](http://alloyteam.github.io/CodeGuide/#project-naming))


## 备注
- 版本：v1.0.0
- 时间：2021-01-18

---------


