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
    div:focus 获取焦点状态,比如input框获取焦点,作用于表单元素
    div:checked 被选中的状态,比如checkbox被选中,作用于表单元素
    div:disabled 被禁用的状态,比如input框被禁用,作用于表单元素
    div:enabled 被启用的状态,比如input框被启用,作用于表单元素
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
    div:target 被选中的元素,比如a标签被选中为锚点时,div:target就是被选中的div元素
    div:lang(en) 被选中的元素
    div:first-line 第一个行
    div:first-letter 第一个字母


## boder和background
-border:
    border-radius:他的原理其实是在四个角上设置圆角(椭圆),圆角的垂直和水平半径就是你设置的值,然后再根据圆角进行切割得到
        border-radius: 10px;四个值:左上,右上,右下,左下
        border-radius: 10px 20px 30px 40px; 四个值:左上,右上,右下,左下
        border-radius: 10px 20px 30px;三个值:左上,右上,右下
        border-radius: 10px 20px;两个值:左上,右上
        border-top-left-radius: 10px;左上,圆角垂直半径为10px,水平半径为10px
        border-top-right-radius:10px 20px;右上,圆角(椭圆)垂直半径为10px,水平半径为20px

    box-shadow:设置盒子的阴影,逻辑上阴影在盒子下面,阴影的模糊半径越大,阴影越模糊,颜色变得越浅

        box-shadow:水平偏移量 垂直偏移量 模糊半径 四个方向上增加阴影大小 阴影颜色
        模糊半径:基于边框两边的位置向两侧同时模糊
        box-shadow: inset 10px 10px 10px 10px rgba(0, 0, 0, 0.5);
        
        
        使用了inset表示内阴影,没有使用inset表示外阴影
        box-shadow:inset 10px 10px 10px 10px rgba(0, 0, 0, 0.5);
        内阴影:你可以理解为阴影在盒子里面,并且除了盒子,其他地方都是阴影
        他的模糊半径是向盒子内模糊,所以模糊半径越大,阴影越模糊,颜色变得越浅

        阴影可以设置多个,多个阴影之间用逗号分隔,每个阴影的属性都是一样的,但是每个阴影的属性可以不一样,哪个最先设置哪个就在最上面