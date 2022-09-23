                                                                                                                                                   字体图标 平面转换 渐变
#### 一.字体图标 使用字体图标实现网页中简洁的图标效果，处理简单的颜色单一的小图（本质是字体，复杂的用css精灵图）

##### 1.1下载字体表后使用引入图标字体样式表  link(同引入css一样 iconfont.css)   调用图标对应的类名              iconfont类(固定)：基本样式，包含字体的使用   icon-xxx图标对应的类名

<span class="iconfont icon-favorites-fill"></span>

1.2图标库没有所需的图标     解决:上传矢量图（svg格式，）在通过购物车添加项目后下载



#### 二.平面转换：transform

(改变盒子平面形态:位移，旋转，缩放)   2D 转换

##### 2.1平移:transform:translate(水平移动距离，垂直移动距离)  取值:像素//百分比(参考盒子自身)  只给一个值则按X方向 

也可单独设置transform:translateX()   绝对定位居中transform:translate(-50%,-50%)   

浮动后的标签具有行内块的特点，宽高自动生效    ||   bgp:right 0;为取图片右边位置
双开门案例中对父级box点击后创建的伪元素子集移动代码.ceshi:hover::after{ transform: translate(100%);   }  中间不要空格

##### 2.2旋转:transform:rotate(角度)  注意角度单位deg    取值为正就是顺时针旋转(需要配合过渡属性才直观)

使用transform-origin属性改变转变原点，默认圆点是盒子中心点

属性名:transform-origin:原点水平位置 原点垂直位置；属性值:方位名词/像素单位/百分比  添加至标签本身

##### 2.3多重转换效果     复合属性:transform:translate()  rotate()  scale();  ！！位置不建议颠倒，旋转会改变坐标轴向，位移方向受影响

先执行位移，旋转就不受影响  ；实现多重转换不要分开写，不要忘了他们都是同一属性名，css具有层叠性

##### 2.4缩放 transform:scale(x轴缩放倍数，y轴缩放倍数)

一般情况下只为scale设置一个值，表示x和y等比例缩放

和平案例中按钮盒子隐藏可以用透明度或display:none   谁过渡改变属性就给谁加transition  由于层叠的存在让margin会简单许多

##### 2.5渐变(颜色桌布变化的视觉效果)

background-img:linear-gradient(颜色1,颜色2)                   !!!!!工作中常用属性值设为 transparent,rgba(0 ,0,0,0.6)

案例中mask类名为遮罩层     产品图片是img  直接给大盒子加渐变色会被直接覆盖掉，所以另创子盒子mask定位



#### 三.空间转换  (改变元素在空间内的形态:位移，旋转，缩放)    z轴位置与视线方向相同,正值对向我们

##### 3.1空间平移transform:translate3d(x,y,z)   属性值:百分比/像素单位       同样也能单独设置transform:translateX() ;

transform:translateX()  translateY()  translateZ() ;

##### 3.2透视   属性名 perspective  (添加给父级)    属性值取像素单位，数值一般在800~1200，透视距离也成为视距，人眼到屏幕距离，数值越小放大效果越明显

##### 3.3空间旋转transform:rotateZ();配合透视属性使用效果才明显

只填transform:rotateZ();与平面旋转实现效果一样，因为中心点没变  　　

###### 中间没有空格　transform: rotateX(-20deg)  rotateY(30deg);　　　❌写法错误 transform: rotate(-20deg,30deg);❌

怎么判断旋转方向   左手法则:左手握住旋转轴，！拇指指向正数方向，手指弯曲方向为旋转正值方向

了解:rotate3d(x,y,z，角度度数):用来设置自定义旋转轴位置及旋转读书

##### 3.4立体旋转  transform-style: preserve-3d;  给父级添加，使子元素处于真正的3D空间，默认值是flat;



旋转导航栏案例中 

！！给橙色盒子旋转后会改变坐标轴向，往上挪变成Z轴方向平移

！！旋转和位移不要分开写，属性名一样会被覆盖掉，用复合属性　　

 transform:translateZ(20px)  rotateX(90deg) ;**！！！别忘了先位移在旋转**

##### 3.5空间缩放　 transform:scaleＸ()；　 transform:scaleY()；　 transform:scale3d(x,y,z)；



#### 四.动画

实现多个状态间的变化过程，动画过程可控(重复播放，最终画面，是否暂停)一刷新即可见效果，不需要配合hover

定义:@keyframes 动画名称   { 动画开始状态可省from {}            to{}          }      两种状态      

​         @keyframes动画名称{0%{} 10%{} 15%{} 100%{}}       多种状态  (百分比是动画总时长的占比)

使用:   **属性名animation: 动画名称  动画时间;**

复合属性:   animation:动画名称 时长    速度曲线(linear匀速//**steps(x)分步**)   延迟时间  重复次数(数字/无限循环infinite) 动画方向(**往返alternate**) 执行完毕状态(默认backwards//**最终状态forwords**);         *不分先后顺序*   有俩时间先动画时长然后延迟时间

了解:拆分写:animation-name    animation-duration   animation-delayA

**animation-play-state:paused;**           为暂停动画，通常配合**:hover**使用

速度曲线:animation-timing-function steps(数字)          ：逐帧动画(一格一格)

多组动画   属性名animation: 动画1，动画2；  精灵跑步案例中animation: move 1s steps(12) infinite**,** run 1s forwards;逗号隔开

走马灯实现无缝动画   看显示区域有多大，把显示区域尺寸 能撑下的图片在复制一下



综合案例中  

 background-position: center 0;让背景图居中   工作中html默认值不是跟游览器一样高   html{ height: 100%;}



#### 五.移动Web

##### 5.1分辨率分类

Ø 物理分辨率是生产屏幕时就固定的，它是不可被改变的

Ø 逻辑分辨率是由软件（驱动）决定的       制作网页参考逻辑分辨率    iphone6/7/8 **逻辑分辨率宽度 375** 物理为750

##### 5.2视口   (目标：使用meta标签设置视口宽度，制作适配不同设备宽度的网页)   pc段端也有视口概念

默认情况下，网页的宽度和逻辑分辨率 不同， 默认网页宽度是980px。

<meta name="viewport" content="width=device-width, initial-scale=1.0">  视口宽度 = 设备宽度/逻辑分辨率  缩放1倍（不缩放）

##### 5.3二倍图 :图片分辨率, 为了高分辨率下图片不会模糊失真

用像素大厨软件测量二倍图中元素的尺寸   现阶段设计稿参考iPhone6/7/8，设备宽度375px产出设计稿。二倍图设计稿尺寸：750px。

##### 5.4百分比布局(流式布局)  效果:宽度自适应，高度固定     （案例:移动端狗东底部导航栏）

##### 5.5Flex布局/弹性布局:能够使用Flex布局模型灵活、快速的开发网页(效果跟基础班浮动一样，但是更方便快捷) 

Ø 是一种浏览器提倡的布局模型           Ø 布局网页更简单、灵活        Ø 避免浮动脱标的问题(浮动最初解决新闻环绕)

缺点是不支持低版本游览器   查看是否兼容caniuse.com

四个组成部分:Ø 弹性容器Ø 弹性盒子Ø 主轴Ø 侧轴 / 交叉轴

**设置方式 Ø 父元素(弹性容器)添加 display: flex;子元素(弹性盒子)可以自动的挤压或拉伸** 

主轴( 默认主轴为横方向)main axis(**弹性盒子都沿着主轴排列**)  Ø 侧轴(竖) / 交叉轴cross axis

盒子之间的距离**调间距**1.可用基础班的margin  2.调轴对齐方式

**5.5.1主轴对齐方式**：

**属性名:justify-content** 属性值:flex-start(默认，从起点依次排) //flex-end//  **center(沿主轴居中排列)**

**space-around(弹性盒子沿主轴均匀排列, 空白间距均分在弹性盒子两侧)**  

**space-between(弹性盒子沿主轴均匀排列, 空白间距均分在相邻盒子之间)**

**space-evenly (弹性盒子沿主轴均匀排列, 弹性盒子与容器之间间距相等)**

**5.5.2.侧轴对齐方式**：

属性名:align-items 属性值:flex-start(默认，从起点依次排) //flex-end//**center(沿主轴居中排列)**//

**stretch (默认值, 弹性盒子沿着主轴线被拉伸至铺满容器,测试的时候子集盒子没高度才看见效果)**



align-self(控制单个子集，给子集添加)：属性值和align-items 一致

盒子尺寸:子盒子没有高度会是默认值stretch，高度跟父级一样，但要是设置了center把默认值stretch层叠，高度由内容填充；没有给宽度由内容填充

伸缩比修改弹性盒子伸缩比:属性名:flex 属性值:整数   注意 : 只占用父盒子*剩余尺寸*   **看子集中flex值一共是多少，再将父级剩余的尺寸分配给各个子集对应的份数**



小兔生鲜移动端项目:

项目准备:1.lib文件夹:存放模板，引入的外部文件(字体图标) 2.创建base.css(清除默认样式)  其他步骤同pc端类似

​                2.引入css样式表,引入字体样式表     引入psd设计图时将像素大厨2×

注意点:

1.由于底部支付部分是固定定位，是托标的，会覆盖在主体内容上面，为了划在最底部支付部分不将版权内容盖住，所以要加主体内容的padding-bottom

2.前期支付部分宽度不写是默认是父级100%，在固定定位后，支付部分脱标，默认宽度转变为内容填充，需要重新填写宽度

支付数额来源于数据库，是变化的，需要单独给他创建标签，否则未来无法替换数据

3.在base.css加入img{100%}控制容器中图片大小，不写图片尺寸也不会撑大

4.在产品图那一栏，给数量定宽高，让内容区域flex:1;设置剩余区域全给到内容，数量区域就自动往右边排 ，红色/红外体温计是变化的，需要另外起标签    游览器最小字号是12px



##### 5.5.3修改主轴方向 (改变元素排列方向)  

属性名:**flex-direction**  属性值:row(水平(默认值))//**column(列, 垂直) **//row-reverse (行, 从右向左)//column-reverse(列, 从下向上)

修改主轴方向后  视觉效果: 垂直居中和水平居中用的属性名记得分得清

##### 5.5.4弹性盒子换行(实现弹性盒子多行排列效果)  弹性盒子过多，弹性容器宽度容纳不下，会自动放缩子集盒子的宽度，最后占满父级容器的一行(默认都要沿主轴排)，体现了弹性布局的特点

**属性: flex-wrap :wrap;**加给父级弹性容器

弹性盒子换行之后,有行默认对齐方式，并不是没有间距的依次排列 

**调整行对齐方式 ：**align-content  Ø 取值与justify-content基本相同()  没有space-evenly



小兔鲜pc项目:

1.侧边栏aside不用写高度，用min-height撑开  

2.上方设置区域不用ul>li 直接标签a套内容

3.订单超出内容显示省略号 ，三个css属性  text-overflow:ellipsis    white-space:nowrap(控制不要换行)   overflow:hiddle 

因为弹性盒子的性质，内容多了会被缩放，给父级加width取值为0,再将剩余flex:1;  或直接量出来给宽       



#### 六.移动适配

​                                     **rem ： 目前多数企业在用的解决方案**                   **vw / vh：未来的解决方案**

##### 6.**1.rem(单位)** 

网页效果Ø 屏幕宽度不同，网页元素尺寸不同（**等比缩放**） 百分比高度适应不了,px是绝对单位

特点:  1.**相对单位**   2.Ø rem单位是相对于HTML标签(根字号)的字号计算结果  3.Ø **1rem = 1HTML字号大小**(先将html标签设置字号)



##### **2.媒体查询**\1. 手机屏幕大小不同，分辨率不同， 设置不同的HTML标签字号(根据视口宽度不同，设置不同的根字号)

**2.1@media** ( **媒体特性**width:320px)  { **选择器**html{ **css样式**font-size:32px } } （缩放设置100%看效果）

**目前rem布局方案中，将网页等分成10份， HTML标签的字号为视口宽度的 1/10**

rem单位的尺寸 = px单位数值 / 基准根字号(小数取三位)

**2.2使用flexible js**配合rem实现在不同宽度的设备中，网页元素尺寸等比缩放效果，核心原理就是根据不同的视口宽度给网页中html根节点设置不同的font-size （省去了为了适配多个尺寸不同的机型手写多次@media的麻烦）

 <script src="../js/flexible.js"></script>



##### 3.**less语法**(为了简化px单位转到rem单位时数值的计算麻烦，css不支持计算写法)

**Less是一个CSS预处理器**, Less文件后缀是**.less**  ，扩充了 CSS 语言, **使 CSS 具备一定的逻辑性、计算能力。**

注意：浏览器不识别Less代码，目前阶段，网页要引入对应的CSS文件。（esay less）

**3.1注释:**

l 单行注释Ø 语法：// 注释内容         Ø 快捷键：ctrl + /   (单行注释无法显现在css中，工作中css是游览器看，人是看less的)

l 块注释    Ø 语法：/* 注释内容 */    Ø 快捷键： shift + alt + A

**3.2运算**

加、减、乘直接书写计算表达式             除法需要添加 **小括号 或 .** 

l 注意：  Ø 表达式存在多个单位以第一个单位为准

**3.3嵌套**（快速生成后代选择器）

.父代选择器{   //父级样式    .子代选择器{       //子代样式       }     }

注意：&不生成后代选择器，表示以当前选择器触发生成，通常配合伪类(hover)或伪元素使用

**3.4变量**

： 把颜色提前存储到一个容器，设置属性值为这个容器名（存储数据，方便使用和修改）。 

l 语法：         1.Ø 定义变量：@变量名: 值;                2.Ø 使用变量：CSS属性：@变量名;

**3.5导入**

引入公共样式  Ø CSS：书写link标签         Ø **Less：导入**

导入: @import “文件路径”;引入less文件，保存后会生成导入文件less对应的css样式。可以省略.less后缀名   不要忘了空格和分号

**3.6导出**(less有单独文件夹，默认Less保存后less和css在同一文件夹下)

方式一:Ø 配置EasyLess插件， 实现所有Less有相同的导出路径

l 配置插件： 设置 → 搜索EasyLess → 在setting.json中编辑 →在less.compole 添加代码（注意，必须是双引号）"out":"文件路径"

 **"out": "../css(文件夹)/"**

**导出单独路径**直接在less里加   // out: ./abc(文件夹)/          // out: ./abc(文件夹)/daqiu.css              文件夹后记得加斜杠

**禁止导出:**例如base.less, common.less    在less文件**第一行**(切记是第一行)添加      **// out: false** 



游乐园项目准备: favicon图标 css文件夹  less文件夹 js文件夹 lib文件夹 images，uploads文件夹  和首页index(normalize.less游览器兼容)

1.引入图标  2.引入字体图标样式表 3.引入css样式 4.引入js 

1.在index.less导入base.less和normalize.less

注意:1.底部工具栏可用footer标签 在less里注意是标签选择器  2.设置根子号变量 @rootSize：37.5rem；

3.活动标题建议装进盒子

4.灰色图片样式 .state.off{}  div.off{}          **在.state里写&.off{}**效果等同于.state.off{}



##### 6.2vw和vh  

特点:相对单位(相对视口的尺寸)   vw：viewport width   1vw = 1/100视口宽度             vh：viewport height  1vh = 1/100视口高度

**vw单位的尺寸 = px单位数值 / ( 1/100 视口宽度 )**  **vh单位的尺寸 = px单位数值 / ( 1/100 视口高度 )**

不能混用，全面屏比例不一样



b站项目

在头部区域z-index:1;配合背景色显示层级  表示一个元素在叠加顺序上的上下立体关系。



#### 七,响应式布局

##### 1.媒体查询           

#####   @media(媒体样式){   选择器 { css  }   }     **Ø max-width     Ø min-width**

1.2.**注意书写顺序**   Ø max-width（从小到大）     Ø min-width（从大到小）



(了解)1.2.媒体查询完整写法  **@media** *关键词   媒体类型 and*    (**媒体特性**) { css}           

关键词：and      only     not      媒体类型:screen       print     speech        all  

 **媒体样式**：视口宽，高width,height     视口最大宽 **max-width**、max-height         **min-width**、min-height          orientation(屏幕方向)

##### **1.3.link引入媒体查询**

<link rel="stylesheet" href="./xx.css" media="(媒体特性)">小括号

##### **1.4.媒体查询，隐藏**

@media (媒体特性) {  隐藏盒子的选择器{  display: none;    }   }



##### 2.BootStrap

2.1简介:前端 UI 框架，它提供了大量编写好的 CSS 样式，允许开发者结合一定HTML 结构及JavaScript，快速编写功能完善的网页及常见交互效果。

2.使用:

2.1link引入<link rel="stylesheet" href="./bootstrap-3.3.7/css/bootstrap.css">      

2.2调用类：使用BootStrap提供的样式     container：响应式布局版心类



##### **3.BootStrap栅格系统**(使用BootStrap栅格系统布局响应式网页)

特点: *栅格化是指将整个网页的宽度分成若干等份       BootStrap3默认将网页分成**12等份***

![image-20220907101636535](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220907101636535.png)



4.BootStrap相关类

**.container**是Bootstrap 中专门提供的类名，所有应用该类名的盒子，默认已被指定宽度且居中。(container类自带内间距15px;)

**.row**类名和**.col类**名定义栅格布局的行和列。(**row类自带间距-15px**)

在案例中，如果不想要container自带的内间距15px,可在容器内在新建类名为row的盒子，其自带的-15px外间距会将内距挤掉

**.container-fluid**也是Bootstrap 中专门提供的类名，所有应用该类名的盒子，宽度均为100%。(同样该类自带内间距15px;)



5.学会BootStrap**全局css样式**的使用(通过 class 设置样式并得到增强效果)

//<table class="基本样式类  具体样式类"> </table>

例如在表格案例中，link引入Bootstrap后，创建表格后，在表格标签内加上对应的BootStrap相关属性可起到美化便捷

   //<table class="table table-striped table-bordered table-hover">对创建的表格，边框，悬停，条纹都做了美化



6.BootStrap**组件** (包括字体图标、下拉菜单、导航、警告框、弹出框等更多功能。)

同全局css样式，程序员复制粘贴大法



**7.BootStrap插件**

**1.引入BootStrap样式    2.引入js文件：jQuery.js+BootStrap.min.js**(**引入顺序有要求**，注意是<srcipt></srcipt>)

3.粘贴结构改内容





项目前期准备:引入样式表先link.BootSrap在css，保证自己的样式权重高 ，

此项目不需要base.css，在BootStrap中就已经有清除默认样式的代码

1.轮播图那一栏  检查元素img{height:auto}，自动跟宽度等比例缩放，要把这个auto层叠掉，层叠方式有两种，将其检查元素的选择器复制进less重新写样式，嫌麻烦直接在img中高度100%!important

2.头部导航栏删除标签元素时，在游览器检查一栏中查看范围     头部导航栏删除css属性时，从外道内一层层检查，不要跳级，

 background-color: transparent;设置背景色为透明,导航栏字体大小，颜色，位置都可在游览器检查找到对应的类名然后在less中做自己的需要的样式

3.导航栏收缩定制功能，找到属性值去BootStrap官网定制一栏对应修改，在重新下载BootStrap框架并引用，(Ctal+F)

4.标题等内容也可在BootStrap找到对应样式，在h标签加class类名h1,h2...

5.开源项目响应式布局间距是靠内容拉开，不是靠div,li盒子拉开，在加入container后，每个盒子的宽度都是25%,已经没有地方再写间距，如果加了会导致换行，达不到需求，在li标签内本身内置了padding-left,padding-bottom



8.全局样式(控制标签样式)可直接调用BootStrap中的样式实现需求，不需要手写或引入公共样式(**直接加类名**，**详情访问网站**)

辅助类:快速浮动，清除浮动，......

响应式工具:

