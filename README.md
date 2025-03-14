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

    border-image:可以给边框设置渐变色或者图片,但是这个属性在实际开发中用的很少,因为他的兼容性不好,所以不推荐使用
    设置border-image属性是必须要有border-width
        
        border-image-source:渐变图片/图片地址   border-image-slice:渐变/图片的宽度   border-image-repeat:渐变/图片的重复方式

        设置渐变:border-image: linear-gradient(to right, red, blue) 1;

        设置图片:border-image: url(./img/bg.jpg) 1;

        设置渐变和图片:border-image: linear-gradient(to right, red, blue) 1 url(./img/bg.jpg) 1;

        设置背景图四个框的中间部分的填充方式:可取值为:stretch(拉伸),repeat(重复),round(圆角),space(空格)

        可以简写为:border-image: url(./img/bg.jpg) 1 stretch;

        border-image-outset:设置边框的向外的偏移量,可以设置四个值,分别是:左上,右上,右下,左下
        
        border-image-width:设置边框背景图片的宽度(不是边框的宽度),可以设置四个值,分别是:左上,右上,右下,左下,默认值为1,设置数值时表示边框宽度的倍数,如果设置为auto,则自动计算为slice的值加px

    background:盒子的背景设置
    
        background-color:盒子的背景颜色
        background-image:盒子的背景图片,使用url()引入,可以使用多张url,一般用于第一张图片加载失败时,加载第二张图片(大小很小,容易加载)
        background-repeat:盒子的背景图片的拉伸方式
            1. repeat（默认值）
            - 背景图片在水平和垂直方向都重复平铺
            - 可能会出现图片被切割的情况

            2. no-repeat
            - 背景图片不重复，只显示一次

            3. repeat-x
            - 背景图片只在水平方向（x轴）重复

            4. repeat-y
            - 背景图片只在垂直方向（y轴）重复

            5. space
            - 背景图片在两个方向重复
            - 图片之间会有均匀的空隙
            - 第一个和最后一个图片会贴着容器边缘
            - 不会切割图片

            6. round
            - 背景图片在两个方向重复
            - 会调整图片大小，使其正好填满容器
            - 不会出现空隙
            - 不会切割图片
        background-size:盒子的背景图片的尺寸:值为图片的宽度,高度,百分比,cover(覆盖,可能会出现图片被切割的情况),contain(包含,可能会出现图片被拉伸/重复的情况),也可以设置为auto(自动),默认值为auto
        background-position:盒子的背景图片的位置,值为图片的左上角位置坐标
        background-attachment:盒子的背景图片的固定方式:值为scroll(滚动),fixed(固定)
        background-origin:盒子的背景图片从哪里开始平铺展开:值为border-box(边框的左上角),padding-box(内边距的左上角),content-box(内容的左上角),默认值为padding-box
        background-clip:盒子的背景图片的裁剪方式:值为border-box(边框),padding-box(内边距),content-box(内容),text(文本区域,需要配合color:transparent使用,但是在谷歌浏览器需要单独设置)
             默认值为border-box,设置背景图片从哪里开始截断,之外的背景图片不显示,如果设置值为text,则文本内容会被融入到背景区域,当设置文字阴影text-shadow时,阴影会在上面

        背景图片默认是相对于容器进行定位的而不是相对于内容,如果想要背景图片相对于内容进行定位,需要设置background-attachment,scroll(相对于容器),local(相对于内容)

        背景设置渐变:
        background-image: linear-gradient(to right, red, blue)/radial-gradient(to right, red, blue);
        
    text:
        text-shadow:文字阴影
        text-shadow:水平偏移量,垂直偏移量,阴影,颜色



