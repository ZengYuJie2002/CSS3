# CSS3
学习CSS3的记录


## CSS3兼容性问题
css3在新推出的时候有很多浏览器是不支持的,支持的浏览器需要使用独特的浏览器前缀来兼容,比如:
-webkit-    : 谷歌浏览器(Chrome),Safari
-moz-       : 火狐浏览器(Firefox)
-ms-        : 微软浏览器(IE)
-o-         : 欧朋浏览器(Opera)

例如使用一个CSS3的属性为了兼容性,我们需要这样写:
div{
    -webkit-border-radius: 10px;//只能针对谷歌浏览器
    -moz-border-radius: 10px;//只能针对火狐浏览器
    -ms-border-radius: 10px;//只能针对微软浏览器
    -o-border-radius: 10px;//只能针对欧朋浏览器
}

在后来浏览器的版本更新,开始慢慢支持CSS3,所以前缀就慢慢被淘汰了,现在我们只需要使用CSS3就可以了,不需要使用前缀了,使用前缀也可以在对应的浏览器中使用(一个属性不加前缀好使,加了前缀一定好使,但是加了前缀好使,不加前缀不一定好使)

我们可以参考[caniuse](https://caniuse.com/)来查看CSS3的兼容性

我们也可以使用一个插件:
- 插件:Autoprefixer
它是一个css后处理器,可以自动为CSS3添加前缀,这样我们就可以使用css3了,不需要手动添加前缀了


预处理器:pre-processor
less,sass,cssnext,先按照它定义好的语法来写,然后它会把语法转换成css3
后处理器:post-processor
postcss+插件,Autoprefixer等,它提供一个环境,它会对我们写好的css代码进行处理,比如添加前缀,压缩代码,合并代码等


## CSS3对选择器增加的功能
关系型选择器模式
-直接子元素模式:div>p
-后代元素模式:div p
-兄弟元素模式:div+p 下一个满足条件的兄弟元素节点
-相邻兄弟元素模式:div~p
-属性选择器:div[test="test"]
-伪元素选择器:
    div::selection 被选中文字的状态
    div::before 在div元素前面插入一个元素
    div::after 在div元素后面插入一个元素
-伪类选择器:
    div:hover 鼠标悬浮状态
    div:active 鼠标点击状态
    div:focus 获取焦点状态
    div:checked 被选中的状态
    div:disabled 被禁用的状态
    div:enabled 被启用的状态
    div:first-child 第一个子元素
    div:last-child 最后一个子元素
    div:nth-child(n) 第n个子元素
    div:nth-last-child(n) 倒数第n个子元素
    div:only-child 唯一子元素
    div:first-of-type 第一个子元素
    div:last-of-type 最后一个子元素
    div:nth-of-type(n) 第n个子元素
    div:nth-last-of-type(n) 倒数第n个子元素
    div:only-of-type 唯一子元素
    div:empty 没有子元素的元素
    div:not(p) 不包含p元素的元素
    div:target 被选中的元素
    div:lang(en) 被选中的元素
    div:first-line 第一个行
    div:first-letter 第一个字母



