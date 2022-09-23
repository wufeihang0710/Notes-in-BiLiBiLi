    web三大样式  html结构  css表现  js行为
### 一:HTML

五大游览器：ie， 火狐，谷歌，safari，opera
1.1基本语法规范   双标签，单标签
1.2标签关系  包含关系，并列关系
3.<!DOCTYPE  html>不是html标签，为声名标签
  <html lang="en">  语言网站  lang="en"   zh-CN

<meta charset="UTF-8"> 万国码
<title></title>网页标题

4.html常用标签  

4.1排版标签 ：标题标签 <h1></h1>   段落标签 <p></p> (两段之间有缝隙)           换行标签 <br />    水平分割线 <hr>
4.2文本格式化标签 ：加粗<strong></strong>  <b></b>   倾斜<em></em>  <i></i>   删除线<del></del> <s></s>  下划线<ins></ins> <u></u>
4.3媒体标签：
   图片<img src=" ./(表当前)"  alt=""  title="" ......>    alt替换文本，图片加载失败时显示alt文本 ; title提示文本，悬停显示 ; width,height(只写一个等比例缩小)   vertical-align可设置图片的垂直对齐方式，值为middle/....
    相对路径：从当前文件开始出发找目标文件的过程    同级./和下级，上级../        绝对路径：从盘符开始，D:\day01\1.jpg
  音频<audio src="" controls></audio>  controls显示播放控件 autoplay自动播放(部分游览器不支持)  loop循环播放
  视频<video src="" controls></video>  controls显示播放控件 autoplay自动播放(谷歌配合muted静音播放)  loop循环播放
4.4链接标签:<a href="./目标网页.html">超链接</a>  (#代表空链接)    target="_blank"跳新窗口  _self(默认，覆盖原网页)
4.5列表标签：
  无序列表：<ul>   <li></li>    <li></li>          </ul>    ul里面只能包含li标签，li可包含任何内容 ，去掉原点属性为list-style:none;
  有序列表：<ol>   <li></li>    <li></li>          </ol>    ol里面只能包含li标签，li可包含任何内容
  自定义列表：（网页底部导航）  dl  dt主题  dd内容   dd默认缩进，dl里面只能包含dt/dd标签，dt/dd可包含任何内容
4.6表格标签：
table 表格整体>> tr  表示行>> td表示单元格       <table border="1">  <tr>  <td></td> </tr> </table>  ,border表示边框宽度   width  height表格宽度，高度(设置推荐css)    
caption表格大标签(写在tr前)，th表头单元格(与td同级)
 表格结构标签：thead表格头部  tbody表格主题 tfoot表格底部     用于包裹tr标签（使游览器执行效率更高）
 合并单元格： 保留左上原则，删除其他的    rowspan跨行合并，colspan跨列合并，属性值是合并单元格的个数  <td rowspan="2"></td>  (只能在同一结构标签使用，不能跨越)
4.7表单标签
标签名:input,  type属性值:text,password,radio,checkbox,file,submit,reset,button  
<input type="text">(单标签)    placeholder占位符  可通过   标签名::placeholder{}设置占位符的css属性
<input type="radio">    name:相同name属性值为一组，只能选一个；checked默认选中
<input type="checkbox">   checked默认选中
<input type="file">  multiple多选
<input type="submit">   value文字     按钮需要配合  表单域标签<form action="">     xxxx     </form>



按钮标签名：button  type属性值：submit,reset,button     <button  type=""> 按钮</button>(双标签)
下拉菜单标签名：select整体，option     <select> <option>北京</option>   <option>上海</option></select>  selceted默认选中，放入option 
文本域标签名：textarea （右下角可缩放） ，cols,rows归定可见宽度和行数（推荐用css）
label标签：绑定内容和表单标签的关系
1.用label把内容包括起来，在表单设置id属性，在lable标签的for属性设置为id 属性值  <input type="radio" name="gender" id="nan"> <label for="nan">男</label>
2.用label把内容和表单一起包裹，删除lable中的for属性     <label><type="radio" name="gender" >男</label>
语义化标签： div     span(网页布局，双标签)
1.div 一行只显示一个
2.span一行可显示多个

4.8语义化标签（了解,多用于手机网页，双标签）
header头部,nav导航,footer底部,aside侧边栏,section区块,aticle文章

5.字符实体
空格 &nbsp;





### 二:CSS基础

CSS 层叠样式表，给页面中的html提供样式，
p段落属性：color,background-color,font-size,width,height,      px像素；  

1.CSS引入方式：
内嵌式：<style>     选择器p   {    属性：属性值；        }          </style>    写在style标签中，style写在head标签里面,title标签下面     小案例
外联式：写在单独的css文件中，通过link标签引入      <link rel="stylesheet" href="./my.css">(放入位置与内嵌式相同)      项目中
行内式：写在标签的style属性中          配合js使用

2.选择器：
标签选择器：选中所有的这个标签都生效
类选择器：.类名{css属性名：属性值;}    <div class="类名">类选择器</div>    (由字母，数字，下划线，中划线) 一个标签可以有多个类名，类名之间用空格隔开,类名可重复，一个类选择器可以选中多个标签
id选择器：#id值{css属性名：属性值;}  配合js使用   <div id="id值">id选择器</div>  所有标签都有id属性，id值在一个页面是唯一的，一个标签只能有一个id值，一个id选择器只能选中一个标签
通配符选择器：*{css属性名：属性值;}     清除margin,padding

3.字体和文本样式：
3.1字体样式：
字体大小：font-size:数字+px(像素)；默认为16px;    字体粗细：font-weight:normal(400)//bold(700)； 字体倾斜：font-style:normal//italic
字体系列： font-family:宋体,黑体,sans-serif(如果没有，，，，)；  常见字体系列（了解）:无衬线字体（sans-serif）,衬线字体（serif）,等宽字体（monospace）
化简：font:style weight size/line-height family;(复合属性)   若要省略只能省略前两个
样式层叠问题：给同一标签设置相同属性，此时样式会层叠，后面的覆盖前面的

3.2文本样式：
文本缩进：text-indent:取值：数字+px(像素)//数字+em(一个字的大小)   
文本水平对齐：text-align:left//center//right;内容对其都可以用（例如：文本，span,a,input,img） ！！！！注意：居中center给以上元素的父元素设置，他们自身不可作为父元素
文本修饰：text-decoration:underline(下划线，常用)  line-through(删除线,不常用) overline(上划线，不常用)  none(无装饰线，常用，例如超链接去除下划线)
行高：line-height:数字+px//倍数(当前字号的倍数，调垂直位置)   

4.调试方式：
css划线表示被层叠覆盖/注释；黄色感叹号表示语法错误；。。。。。

5.拓展：颜色
常用:十六进制表示法：  #6位(两两为一组:依次为红,绿,蓝)    rgba表示(三原色＋透明度（取值0~1）)
标签div,p,水平居中:margin:0 auto;





### 三:CSS进阶

1.选择器进阶
复合选择器
   后代选择器：空格  ;语法： 选择器1 选择器2{ css }；选择父元素后代中满足条件的元素
   子代选择器：>      ;语法：选择器1>选择器2{ css }；选择父元素儿子中满足条件的元素
   并集选择器：,        ;语法：选择器1，选择器2{ css }；选择多组标签设置同样样式
   交集选择器：紧接着 ;语法：选择器1选择器2{ css }；选中满足多个选择器的标签
hover伪类选择器：鼠标选中的标签设置样式   语法：选择器:hover{css} (任何一个标签都可以选择伪类)
emmet语法:

2.背景相关属性
  背景颜色
  背景图片：语法：background-image:url(xxx.jpg);
  背景平铺：语法：background-repeat:repeat(默认，水平和垂直方向都平铺)//no-repeat//repeat-x//repeat-y;
  背景位置：语法： background-position:水平位置 垂直位置;(方位名词（left//center//right  top//center//bottom）//x y值（px   0px）)
  化简： background:color image repeat position;(复合属性，不分先后顺序)   

3.元素显示模式
  块级元素div:独占一行，!!!!宽度默认是父元素的高度，高度默认由内容展开，可设置宽高  （div, p,ul,li,dl,dt,dd,form,header,footer）
  行内元素span:一行可以显示多个，高度，宽度由内容展开，不可以设置宽高(a,span,b,u,i,del)
  行内块元素:一行可显示多个，还可设置宽高(input,textaea,button,select,img)

 元素转换：display:block(转块，多次)//inline-block(转行内块，较多)//inline(转行，较少)
拓展：html嵌套规则：
   1.块级元素一般作为大容器，可嵌套：文本，块，行，行内块,(p标签不要嵌套div,p,h)    
   2.a标签可嵌套任意元素，除a 之外-

4.css特性
4.1继承性:子元素默认继承父元素样式的属性；文字控制属性都能继承（与字相关的都继承）
注意：a标签继承颜色会失效，标题继承字号会失效
4.2层叠性：
样式冲突时：选择器优先级相同时，才能用层叠性判断结果。
4.3优先级:当一个标签选择了不同的样式冲突的选择器决定谁生效
继承<通配符选择器<标签选择器<类选择器<id选择器<行内样式<!important(写在属性值后面,分号前面,不要给继承添加，否则无效)
若复合选择器冲突，数（行内样式，id选择器,类选择器,标签选择器）依次比较各个复合选择器，权重相同时比较层叠性，都是继承看直接父级



### 四:盒子模型

                                布局从外到内，先宽高背景色，放内容，调节内容位置，控制文字大小，颜色等细节

盒子模型:网页中的每一个标签都可以看作是一个盒子，通过盒子的视角进行布局
CSS：内容区域(content,蓝色),内边距区域(padding,绿色),边框区域(border,黑色),外边距区域(margin,橙色)构成
1.内容content
  设置高度和宽度  属性：width,height
2.边框border     复合属性：border  取值无顺序：10px(粗细)  soild//dashed//dotted(线条种类)  red;
  若只给盒子特定方向设置边框线  属性：border-方位名词  取值相同
  了解：还可有单个属性 border-width/style/color
  盒子的最终尺寸是本身属性width/height+边框属性width
3.内边距padding  同border一样，会撑大盒子
   可为复合属性：(单独设置某个方向的内边距)padding:  px px px px(上，右，下，左);//px px px(上，左右，下);//px px(上下，左右);顺时针，没有看对面
  用padding灵活撑开距离

  内减模式：对于内边距和边框会自动撑大盒子问题，不想手动减去可选择自动内减:box-sizing:border-box;
4.外边距margin   设置方法和内边距一样

清除默认内外边距  场景:(p标签,h标签，ul-li标签)
*{  padding:0;margin:0}
版心居中:网页的有效内容(水平方向) margin:0 auto;

外边距折叠现象:
外边距合并问题:垂直布局的块级元素，上下的margin会合并,最终两者距离取最大值   解决方法:只给其中一个盒子设置Margin
塌陷(坑爹)现象:互相嵌套的块级元素，子元素的margin-top会作用在父元素上，导致父元素一起向下移动  解决:加给父元素加border-top或padding-top//给父元素设置overflow:hidden//转换成行内块元素(多此一举)//设置浮动
行内元素的内外边距问题：想要通过padding或者margin改变行内标签垂直！！！位置无法生效  解决:设置行高



### 五:CSS浮动

                                       浮动后的标签具有行内块的特点，宽高自动生效



1.结构伪类选择器:利用标签的关系寻找元素，减少HTML对类的依赖，保持代码简洁；场景:用于查找某父级选择器中的子元素

选择器::first-child{}:匹配父元素中的第一个子元素  last-child{}  ;    nth-child(n){};       nth-last-child(n){};

n除选单个数的注意点：偶数2n,even  奇数2n+1,2n-1,odd   前x个-n+x(x取任意值)    找第5个往后 n+5



2.伪元素：由CSS模拟出的标签效果  场景:页面的非主体内容（装饰性内容）可使用伪元素；必须设置content属性生效，默认是行内显示模式

::before 在父元素内容的最前添加一个伪元素

::after 在父元素内容的最后添加一个伪元素



3.标准流:标签的默认排列规则



4.浮动：网页布局   （传统：两个div转行内块换行后显示效果有缝隙  解决：加属性float: 值left;）

特点：浮动元素会脱离标准流，在标准流中不占位置，浮动比标准流高半个级别，可覆盖标准流中的元素

​            浮动找浮动，下一个浮动元素会在上一个浮动元素后面左右浮动，

​             浮动标签是顶对其的

​             浮动有特殊效果：一行显示多个，可设置宽高（浮动后的标签具备行内块特点）

注意点:不能用text-alian:center 和margin:0 auto;(无法水平居中浮动比标准流高级 解决：另加div标签成父级设置)



CSS书写顺序:1.放浮动或display 2.放盒子模型相关属性padding content border margin 3.文字样式(游览器执行效率更高)

网站主导航必须用li嵌套a

5.清除浮动：清除浮动带来的影响  场景:如果子元素(左右div)浮动，此时子元素不能撑开标准流的块级父元素(父级div没有高度)（父子级标签，自己浮动，父级没有高度，后面的标准流(如div)后影响，显示到上面的区域）

解决：

1.父级设置高度 

2.额外标签发:(在父元素内容最后添加一个块级元素，给添加的块级元素设置clear:both//left//right) 类名clearfix

3.单伪元素清除法  .clearfix::after{content:'';display:block;clear:box;}   height:0;visibility:hidden;

4.双伪元素清楚法: .clearfix::after, .clearfix::before{content:'';display:table;}.clearfix::after{clear:both;}(解决外边距塌陷问题)

5.给父元素设置overflow:hidden

项目开发：	一：根目录  1.images  2.css  3.index.html





### 六 :CSS定位



                                                  网页的三种布局方式：标准流，浮动，定位。

1.CSS定位：

作用：用于盒子之间的层叠情况，可以让盒子始终固定在某个区域

2.设置方式设置定位方式 属性名:position   属性值:relative相对定位//absolute绝对定位//fixed固定定位//static静态定位

设置偏移量:设置俩方向  水平和垂直 （left//right,top//bottom）  xx+px; 如果同一方向都写了 ，去top和left.



3.相对定位：相对于自己之前的位置移动   position:relative;

特点：1.占有原来的位置 仍然具有标签原有的显示模式特点2.相对于自己原来位置进行移动 3.在页面中占位置 → 没有脱离标准流



4.绝对定位（拼爹形）   相对于非静态定位的父元素进行定位移动  position:absolute

就近先找已定位的父级，如果有这样的父级就以这个父级为参照物进行定位；有父级但是没有定位，就以游览器为参照物进行定位(子绝父相)

特点：1.在页面中不占位置 → 脱离标准流 2.改变标签的显示模式，具有行内块特点 



绝对定位的盒子不能使用margin:0 auto;来居中         

解决：普通做法：left,top取50%，然后用margin-left,margin-top取负数,值为盒子高宽的一半  缺点：子盒子宽度变化后需要重新改代码

优化做法：transform:translate(-50%,-50%)优点：表示沿着水平和垂直始终移动自己宽度的一半，子盒子宽度变化不需要更改代码



5.固定定位：死心眼型定位，相对于浏览器进行定位移动  position:fixed;

特点：1具备行内块特点（必须设置宽度和高度）.  2相对于浏览器可视区域进行移动 3在页面中不占位置 → 已经脱标



6.元素的层级关系:

不同布局方式的层级关系标准流<浮动<定位

不同定位之间的层级关系:相对，绝对，固定默认层级相同  此时HTML写在下面的元素层级更高，会覆盖上面的内容

z-index:整数，取值越大，显示顺序越靠上，默认值是0，(必须配合定位才能使用)





### 七:CSS装饰

 CSS装饰：

游览器解析行内标签，行内块标签都当作文字处理，垂直方向都默认基线对齐，导致垂直方向无法正常居中/对齐

1.垂直对齐方式   属性vertical-align  属性值:baseline(基线对齐，默认) top middle(常用) bottom

display:block也或许能解决，让游览器认为块标签

让图在垂直方向居中，先给父级加行高与父级高度一样，再给图片加vertical-align,水平居中可用

**项目中 vertical-align 可以解决的问题**

\1. 文本框和表单按钮无法对齐问题

\2. input和img无法对齐问题

\3. div中的文本框，文本框无法贴顶问题

\4. div不设高度由img标签撑开，此时img标签下面会存在额外间隙问题

\5. 使用line-height让img标签垂直居中问题



2.光标类型

属性名：cursor  属性值:default(默认)  pointer(小手) text(工字形) move(十字光标)



3.  

➢ 画一个正圆：\1. 盒子必须是正方形  \2. 设置边框圆角为盒子宽高的一半 → border-radius:50%(最大取到50%)

➢ 胶囊按钮：\1. 盒子要求是长方形  \2. 设置 → border-radius：盒子高度的一半



**溢出部分显示效果**

溢出部分：指的是盒子 内容部分 所超出盒子范围的区域

➢ 场景：控制内容溢出部分的显示效果，如：显示、隐藏、滚动条……

➢ 属性名：overflow

属性值  visible默认，溢出内容可见  hidden 溢出部分隐藏  scroll无论是否溢出，上下左右都显示滚动条 auto根据是否溢出，自动显示或隐藏滚动条  

父子集标签隐藏子集溢出部分给父级加overflow:hidden



**5.1 元素本身隐藏**

场景：让某元素本身在屏幕中不可见。如：鼠标:hover之后元素隐藏

➢ 常见属性：

\1. visibility：hidden   占位置隐藏效果，工作中不常见

\2. display：none 不占位隐藏，工作中常见

在二维码案例中，给图片设置dispaly:none 再给他的父级a标签设置鼠标悬停显示  加css 为a:hover img{ display:block;}

6**（拓展）元素整体透明度**

➢ 场景：让某元素整体（包括内容）一起变透明

➢ 属性名：opacity    ➢ 属性值：0~1之间的数字 1：表示完全不透明 0：表示完全透明

➢ 注意点：opacity会让元素整体透明，包括里面的内容，如：文字、子元素等……



7.精灵图  场景:项目中将多张小图片合成一张大图      优点:减少服务器发送次数，减轻服务器压力

使用步骤:常见一个盒子，设置盒子的尺寸与小图尺寸相同   将精灵图设为盒子的背景图片  修改背景图位置

精灵图的标签都用行内标签(span,a,i)

创建行内标签 设置行内标签CSS属性，转显示模式ｂｌｏｃｋ，设置宽高，设置背景图片，用background－position调节位置：两个数值取负数　



8.背景图片大小设置 background-size:高度 宽度。 取值:数字+px//百分比(相比盒子尺寸)//contain(等比例缩放，直到不会超出盒子最大)//cover(覆盖，直到刚好填满盒子无空白)

背景连写复合属性background:color image repeat position/size



9.盒子阴影属性设置box-shadow:  属性值h-shadow(必须,水平偏移量) v-shadow(必须,垂直偏移量) blur(透明度) spread(阴影扩大) color inset(改为阴影内部)  前四个都是  数字+px



10.过渡：让元素缓慢变化，增强交互效果，长配合hover使用

(谁变化谁加过渡属性)属性名:  transition：all（变化属性比较多，懒得写可选all） //width       过度时长:数字+s   

例如改盒子宽度和背景色   在布局里加transition：width 1s,background-color 2s;        在配合hover{}里改变化后的宽度和颜色



11.骨架结构<!DOCTYPE html>文档类型说明 告诉游览器该网页的html

<html lang="en">搜索引擎+游览器翻译  zh-CN

<meta charset="UTF-8">万国码


<meta name="viewport" content="width=device-width, initial-scale=1.0">宽度=设备宽度 移动端网页要用




12.SEO三大标签  搜索引擎优化 作用让网站在搜索引擎排名靠前

提升SEO常见方法：1.竞价排名 2.把网页制作成html后缀 3.标签语义化(在合适的地方放合适的标签)

<meta name="desription" content="....">

title 网页标题标签                      desription     网页描述标签                  keywords 网页关键词标签



13.icon图标

<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">

图片格式为icon  放在根目录下





### 八:项目准备



项目文件准备：

1.新建 xtx-pa-client   （项目根目录，项目文件夹不建议用中文）

2.favicon.icon图标

3.images：存放网站固定使用的图片素材，如logo，样式图片 ，精灵图          uploads：存放网站非固定使用，如商品素材

4.新建index.html 

5.新建css文件夹      base.css基础公共样式（清除默认样式的代码） common.css该网站中多个网页有相同模块的重复样式，如头部，尾部  index.css主页样式



项目代码准备

1.引入样式表:link....按顺序引入，即base.css   common.css   index.css

2.引入SEO三大标签  title 网页标题标签   desription     网页描述标签   keywords 网页关键词标签  link.favicon引入图标

3.清除默认样式代码    复制粘贴即可   内减模式/默认字号/字号颜色/超链接清除下划线/默认列表样式/左浮动、右浮动  行高默认1.5倍



1.确定版心的宽度 设置wrapper 写在common.css中

2.网页最上面为 快捷导航shortcut   如果需要全宽背景色另嵌套一个类直接叫wrapper往里面放内容 在css中写.shortcut .wrapper{}确定样式    ，写完一个部分可收缩

3.小兔生鲜中快捷导航中小图片用  span 标签中设置css 背景图  小图片微调用游览器可直接检查工具，span里的图和后面文字垂直对不齐，图和字对不齐用vertical:middle 图和字贴太紧在span的css设置margin-right 

4.给logo那一栏区域命名为header  header中设置上下间距用margin时注意不要把wrapper属性覆盖掉 创建类名为xxx的div标签可直接  .xxx    导航区域建议不要定宽

.Logo用h1盒子嵌套  h1嵌套a，里面写网站名称，为了提升seo，再把logo写进a的背景图  在用font-size设置为0把网站名称消除    h1是网页最重要的标题    

ul>li>a

搜索栏区域  直接input占满然后放大镜可以用定位或者放大镜用span标签   注意border不要被覆盖，放内容地方就得减小  input文本框也可设置padding让文字缩进        用定位时不一定创建div，也可span    绝对定位子集本身就具有行内块标签特点，span设置没必要再加display

5.网页尾部底部为版权区域  需要全宽背景可以同上一样  记得改宽度 

价格优惠等标语因为图和文字格式一样 也可用ul,li  发现他们尺寸不一样应该取最大  结构伪类选择器选同级   同级别li   图也可用伪元素,默认行内创建，需要的时候转显示模式   关于图和字高度不一，记得vertical /line-h  都试过还是对不齐，定位浮动

第二个li里面的before添加背景图位置属性 .foot .top li:nth-child(2)::before

尾部超链接和版权直接用俩p嵌套直接加a就行，后面的描边直接写竖杠|   <p>  a标签 |    a标签 | ....</p>因为尾部不需要优化    



6.banner轮播图部分 ul>li  每个li里面放一张图片，想单机跳转就加超链接  5张图就有5个li  侧导航栏，箭头等元素用CSS定位

侧导航 aside    block定义后宽度与父级一样   盒子左右箭头不一定非要用div标签 可直接用a标签后转显示模式 前一个类命名为prev  后一个为next  

左右箭头样式一样 可选用并集选择器   .prev .next{ css}可化简代码  半透明 rgba

背景图位置负责两件事，改变箭头在盒子里的位置；改变精灵图的位置，导致在精灵图中测量的尺寸不准确    a负责盒子，加span负责箭头/游览器检查.

banner底下的原点用ol>li  哪个白表示当前状态，类名用active/current js找到用户电机的li，添加类名 li变成白色



7.新鲜好物标题引导命名为hd  为header缩写，内容命名为bd （不确定内容不用加高，靠内容自动撑开）在ui>li*4浮动后由于父级没有高，不方便给，会出现浮动托标，要清除浮动  标题区域用line-height撑开，

后面新鲜出炉等内容用span嵌套，不用单独加p     查看全部后的精灵图用伪元素(行内)

以后俩字号连在同一区域且字号不一样 直接另一个加span，不用每个都给格式

偏的原因看跟谁对齐，

内容用li加宽高

善于使用并集选择器化简





