#### 一:Web APIs 和 JS 基础关联性

##### 1.API 和 Web API

 简介:**ECMAScrip**(JavaScript语法)                 **DOM**(文档对象模型)      **BOM**(浏览器对象模型)   **后两种属于Web APIs**     

2.什么是API(应用程序编程接口)

一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。简单来说：**API 是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。**

3.什么是**Web API**(浏览器提供的一套操作**浏览器功能**和**页面元素**的 **API** ( BOM 和 DOM )。)

MDN 详细 API : https://developer.mozilla.org/zh-CN/docs/Web/API

因为 Web API 很多，所以我们将这个阶段称为 **Web APIs**

Web API 一般都有输入和输出（函数的传参和返回值），Web API 很多都是方法（函数）



#### **二.DOM**

**1.DOM**(**文档对象模型**：是 W3C 组织推荐的处理可扩展标记语言（HTML或者XML）的**标准编程接口**。)

W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以**改变网页的内容、结构和样式。**

特点:1.DOM 就是把「文档」当做一个「对象」来看待                  2.DOM 的顶级对象是 document

​         3.DOM 主要学习的是操作页面元素                                         4.DOM 是 W3C 标准规范

 **2.DOM 树**

![image-20220909120257790](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909120257790.png)

文档：一个页面就是一个文档，DOM 中使用 document 表示 

元素：页面中的所有标签都是元素，DOM 中使用 element 表示 

节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM 中使用 node 表示

DOM 把以上内容都看做是**对象**



**3.获取元素**(DOM在我们实际开发中主要用来操作元素。)

 根据 ID 获取                根据标签名获取                       通过 HTML5 新增的方法获取               特殊元素获取

3.1 根据 ID 获取          document.**getElementById('id');**

使用 **getElementById()** 方法可以获取带有 ID 的元素对象。****参数 id是大小写敏感的**字符串**

注意:返回的是一个元素对象Object        

// <div id="time">2019-9-9</div>     因为我们文档页面从上往下加载，所以先得有标签,所以我们script写到标签的下面

// <script>    var timer = **document**.getElementById('time');      </script>

 **console.dir 打印返回元素对象**,更好的查看里面的**属性和方法**   **console.dir**(timer);  div#time



3.2 根据标签名获取             document.**getElementsByTagName**(**'标签名');**

返回带有指定标签名的**对象的集合**。以**伪数组**的形式存储的,遍历的话用for(var k in 对象名)

注意:如果页面中没有这个元素,返回的是空的伪数组的形式underfined

指定某个元素(父元素)内部所有指定标签名的子元素，获取的时候不包括父元素自身**父元素.getElementsByTagName('标签名');**



3.3 通过 HTML5 新增的方法获取 (只支持ie9以上)   document.**getElementsByClassName(‘类名’)**；

document.**querySelector('选择器');**        // 根据指定选择器**返回第一个元素对象**    案例: **.box**  **#id**    **li**

document.**querySelectorAll('选择器');**   //根据指定选择器返回



3.4获取特殊元素（body，html）

doucumnet**.body**  // 返回body元素对象                  document**.documentElement**  // 返回html元素对象



**4.事件基础(事件是可以被 JavaScript 侦测到的行为)   简单理解： 触发--- 响应机制。**

4.1事件三要素:**事件源 （谁）**        **事件类型 （什么事件）**              **事件处理程序 （做啥）**

(1) 事件源 事件被触发的对象按钮           

(2) 事件类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过 还是键盘按下

(3) 事件处理程序通过一个**函数赋值的方式完成**

   var btn = document.getElementById('btn');  **//获取事件源**

   btn.onclick**//绑定事件** = function() {alert('点秋香');**//添加事件处理程序** }

![image-20220909152113374](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909152113374.png)



**5.操作元素(注意以下都是属性)**

**5.1 操作元素内容**

element**.innerText**            从起始位置到终止位置的内容, 但它去除 html 标签， 同时空格和换行也会去掉

element**.innerHTML**          起始位置到终止位置的全部内容，能识别更换内容后的html 标签，**同时保留空格和换行,保留原样**

注意区别: div.innerHTML = '<strong>**今天是：**</s.trong> 2019';



**5.2操作元素属性**

​      1. src、href           2. id、alt、title

案例: img.src='../code/images/open.png';



**5.3** **操作表单元素的属性**表单里的值通过value属性保存，innerhtml无效

type类型、value值、checked选择、selected选择、disabled使用        案例中:this 指向的是事件函数的调用者 this.disabled = true;btn

案例:  input.type='input';



5.4 **操作样式属性**(通过 JS 修改元素的大小、颜色、位置等样式。)

JS 里面的样式采取驼峰命名法 比如 fontSize、 backgroundColor

 element**.style**  行内样式操作                 element**.className** 类名样式操作

**5.4.1** element**.style**  行内样式操作(适用于样式比较少，功能简单的情况) 

例如:  this.style.backgroundColor = 'purple';

注意:JS 修改 style 样式操作，**产生的是行内样式，CSS 权重比内嵌式高**

精灵图案例中，获取元素的方法返回的是一个包含多个li的伪数组，通过索引号为每个数组修改不同的精灵图坐标

京东输入框案例中，input输入框里的value代表了值，不属于style里的属性范畴，直接写this.value='';不要写this.style.value='';

还有不要用placeholder占位符,手机默认内容也可能作为搜索的值



5.4.2  element**.className** 类名样式操作  (会直接更改元素的类名，会覆盖原先的类名。)

this.className = '**类名**'                        

注意:**类名必须在style里声明**; 如果想要保留原先的类名做多类名选择器  this.className = '原类名 新加类名';





##### 6.排他思想

1.所有元素全部清除样式（干掉其他人） 2. 给当前元素设置样式 （留下我自己） 

利用for循环为每一个事件源注册事件类型

百度换肤案例:

网页身体背景设置样式  body.style.backgroundImage='**url('+ this.src+')** '          url(this.src)//string

在之前的精灵图案例中背景图位置设置样式   lis[i].style.backgroundPosition = **'0 -' + index + 'px'**    (0 -index)//number

隔行换色案例:

用到新的鼠标事件：**鼠标经过 onmouseover//鼠标离开 onmouseout**

var trs = document.querySelector('tbody').querySelectorAll('tr');//获取元素获取的是 tbody 里面所有的行



**表单全选取消全选案例:**

**全选和取消全选做法：**  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可

**关键点在于对全选按钮做注册事件，遍历下面复选框，让复选框checked状态与全选框保持一致( select[i].checked=this.checked;)**

**下面复选框需要全部选中， 上面全选才能选中做法**： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。

关键点在于一开始遍历下面复选框，为每一个复选框注册事件，每一个复选框事件触发后，记录一个变量为true,在遍历一次整个复选框，如果一旦发现一个未被选中(判断语句**!select[i].checked**)，即复选框的checked为false,就把变量设置为false,最后让全选框的checked的状态为那个布尔型变量。如果if语句被执行，，还可以加break,提高执行效率；



##### 8.获取自定义属性

  8.1获取属性值                

​    element.属性//element['属性']       获取**内置属性值**（元素本身自带的属性）

​    element.**getAttribute('属性')**;  主要获得自定义的属性，程序员自定义的属性，例如定义<div index="1"></div>**index为自定义**

  8.2设置属性值 

​     element.属性 //element['属性'] = ‘值’            设置内置属性值。         注意:如果是属性是类名，还可以通过元素.className='更改值'

​     element.**setAttribute('属性', '值');**                  主要设置自定义的属性   

  8.3移除属性值

​     element.**removeAttribute('属性');**

Tab栏切换案例:

不要把关键字top用作变量名,在切换导航栏显示对应模块中，直接在for循环里的设置 ii[i].style.display = 'block';i的作用域不一样，例如console.log输出i会是undefined，所以会ii[i]会报错，且无法直接得到i的值。解决办法:在for循环中为每一个td设置自定义属性index，并将它赋值为i,代码: **td[i].setAttribute('index',i);** 后续在添加一个变量存储获取这个自定义属性的值，在设置**ii[index].style.display = 'block';**





**自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。**

##### 9.H5自定义属性(但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性。)

9.1  H5规定**设置自定义属性******data-****开头做为属性名并且赋值。

例如<div data-index="1" data-list-name='andi'></div>   

9.2H5新增element.**dataset.**index  或者 element.**dataset**[‘index’]  ,**ie11才开始支持** ,dataset 是一个集合里面**存放了所有以data开头的自定义属性**           

注意:如果自定义属性里面有多个-链接的单词，我们获取的时候采取 **驼峰命名法**(例如下面的nameList)

 例如:div.**dataset.index**  //  div.**dataset['index']**          div.**dataset.nameList**



##### 10.节点操作

10.1获取元素通常使用两种方式：

1. 利用 DOM 提供的方法获取元素(逻辑性不强、繁琐)
2. 利用节点层级关系获取元素(利用**父子兄节点关系**获取元素逻辑性强， 但是兼容性稍差)

HTML DOM 树中的所有节点均可**通过 JavaScript 进行访问**，所有 **HTML 元素,元素的属性（节点）均可被修改，也可以创建或删除。**

一般地，节点至少拥有**nodeType（节点类型**）、**nodeName（节点名称**）和**nodeValue（节点值）**这三个基本属性。

类型:**元素节点nodeType为1**    属性节点nodeType为2       文本节点nodeType为 3(文本节点包含文字、空格、换行等）



10.2节点层级

  10.2.1父级节点

node.**parentNode**      可返回某节点的父节点，注意是**最近的**一个父节点如果指定的节点,没有父节点则返回 null 

案例:var erweima = document.querySelector('.erweima');   console.log(**erweima.parentNode**);



  10.2.2. 子节点

parentNode.childNodes（标准）  childNodes **所有的子节点** 包含 元素节点 文本节点(甚至换行),等等

parentNode.**children**，是一个**只读属性**，返回所有的**子元素节点**。它只返回子元素节点，**其余节点不返回** 



  10.2.3子节点的第一/最后

 parentNode.**firstChild** //**lastChild**  返回**第一个子节点**//**最后一个子节点**，找不到则返回null。也是包含所有的节点。

parentNode.**firstElementChild**//**lastElementChild**  返回**第一个子元素节点**//**最后一个子元素节点**，找不到则返回null。**兼容问题,ie9**

 方便的有兼容性问题，**实际开发中** console.log(**ol.children[0]**);    //ol标签有若干个li标签，拿到第一个和最后一个li标签写法

​                                                            console.log(**ol.children[ol.children.length - 1**]);



新浪下拉菜单案例:在选中li中,对选中他的父元素节点ul通过tagname或者类名的方法为什么会报错???

​                               注意细节，逗号，点号，block分清楚,不然bug找起来烦死人！！

如果通过排他思想，先把每一个li的第二个元素孩子隐藏掉，再把鼠标经过的li孩子显示为block，当鼠标离开后，li的第二个孩子会一直显示，可能效果不是特别令人满意。最好的方法还是鼠标经过就显示，鼠标离开就隐藏！！



10.2.4兄弟节点  

 node.**nextSibling**//**previousSibling** 返回当前元素的下一个//上一个兄弟节点，找不到则返回null。同样，也是包含所有的节点。

node.**nextElementSibling**//**previousElementSibling** 返回第一个//上一个**兄弟元素元素**节点，找不到则返回null。   **兼容问题,ie9**

 没有很好的解决办法，只能自己封装一个兼容性的函数，把元素传进来，对元素的下一个节点进行筛选，如果下一个兄弟节点的节点类型是1；就return ;



##### 10.3创建节点

document**.createElement(**'tagName**')**方法创建由 tagName 指定的 HTML 元素。因为这些元素原先不存在，是根据我们的需求动态生成的，所以我们也称为**动态创建元素节点**。

案例:var li=document**.createElement('li');**

##### 10.4添加节点

node.**appendChild**(child)   将**一个节点添加到指定父节点的子节点列表末尾 **   node是父级，child是子集，类似于 CSS 里面的 after 伪元素。  后面追加元素，类似于数组中的push

案例: ul.**appendChild(li);**

node**.insertBefore**(child, 指定元素)  将**一个节点添加到父节点的指定子节点前面**。类似于 CSS 里面的 before 伪元素。

案例:ul.**insertBefore(lili, ul.children[0]);**



留言板案例:

核心思路： 点击按钮之后，就动态创建一个li，添加到ul 里面。

创建li 的同时，把文本域里面的值通过li.innerHTML 赋值给

 li如果想要新的留言后面显示就用 appendChild 如果想要前面显示就用insertBefore

##### 10.5删除节点

 node**.removeChild(child)**   从 DOM 中删除一个子节点，返回删除的节点。

案例:ul.**removeChild(ul.children[0]);**

##### 10.6复制节点

node.cloneNode()   返回调用该方法的节点的一个副本。 也称为克隆节点/拷贝节点

注意:括号为**空或者里面是false 浅拷贝** **只复制标签不复制里面的内容**

ul.**children[0].cloneNode(true);**  括号为true,深拷贝,复制标签复制里面的内容

案例:ul.children[0].**cloneNode(true);**   //复制节点和创建节点一样，都不会直接显示，哈需要添加节点在某个区域

动态创建表格案例:在获取tbody标签通过query和tagname方式返回值不一样？？？

 td.innerHTML = '<.**a href="javascript:;">删除 </a>';**

点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  

​        tbody.removeChild(this.parentNode.parentNode)



##### 11.三种动态创建元素区别

document.write()    案例: document.write('<div>123</div>');  如果页面文档流加载完毕，**再调用这句话会导致页面重绘**                   

element.innerHTML    inner.innerHTML = '<.a href="#">百度</a>'      innerHTML 创建多个元素效率更高（不要拼接字符串，采取**数组形式拼接**），结构稍微复杂       

document.createElement()   createElement() 创建多个元素效率稍低一点点，但是结构更清晰



#### 三.事件高级

##### 1.注册事件（绑定事件）

传统方式:利用 on 开头的事件onclick,唯一性

方法监听注册方式:**addEventListener()** 它是一个方法,**ie9**以上支持,**同一个元素同一个事件可以注册多个监听器**

**1.2 addEventListener 事件监听方式**

eventTarget(目标对象).addEventListener(**'type', listener**[, useCapture])

type：事件类型字符串，比如 click 、mouseover ，**不要带 on**,**加引号**

listener：事件处理**函数**，事件发生时，会调用该监听函数

useCapture：可选参数，是一个布尔值，默认是 false。

1.3(了解)attachEvent 事件监听方式(IE8 及早期版本支持)太冷门，不建议使用

​         eventTarget.attachEvent(eventNameWithOn, callback) 

​         eventNameWithOn：事件类型字符串，比如 onclick 、onmouseover ，这里要带 on

​         callback： 事件处理函数，当目标触发事件时回调函数被调用

##### 2.删除事件(解绑事件)

2.1传统注册方式   eventTarget**.onclick = null;**

2.2方法监听注册方式 

2. 2.1eventTarget.**removeEventListener('type', listener**[, useCapture]);

案例:   divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号

​            function fn() {

​            alert(22);

​            divs[1].**removeEventListener('click', fn);**

​    }

2.2.2eventTarget.**detachEvent**(eventNameWithOn, callback);  这里要带 on



##### 3.DOM事件流(**事件**发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 DOM 事件流。)

事件流描述的是从页面中接收事件的顺序。

事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 DOM 事件流。

![image-20220911093931496](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911093931496.png)比如我们给一个div 注册了点击事件：

DOM 事件流分为3个阶段： **1. 事件捕获阶段         2. 当前目标阶段          3. 事件冒泡阶段**(从小事件源到整个文档) 

注意:1.JS 代码中只能执行捕获或者冒泡其中的一个阶段。

​        2.onclick 和 attachEvent 只能得到冒泡阶段。

​        3.addEventListener(type, listener[, useCapture])第三个参数如果是 true，表示在事件捕获阶段调用事件处理程序；如果是 false（不  写默认就是false），表示在事件冒泡阶段调用事件处理程序。

​       4.实际开发中我们很少使用事件捕获，我们更关注事件冒泡。有些事件是没有冒泡的，比如 onblur、onfocus、onmouseenter、onmouseleave

##### 4.事件对象

简介:事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象 event，它有很多属性和方法。

案例:eventTarget.onclick = function(**e**/evt/event) {  }

注意:1.**event是个形参**，系统帮我们设定为事件对象，**不需要传递实参**过去。

​         2.当**注册事件时,event 对象就会被系统自动创建**，并依次传递给事件监听器（事件处理函数）。

​         3.事件对象也有兼容性问题 ie678,通过 window.event 兼容性的写法  e = e || window.event;



##### 5.事件对象的常见属性和方法

5.1 e.target 和 this 的区别:          this 是事件绑定的元素,这个函数的调用者          e.target 是事件触发的元素.指向点击对象。

案例中:ul嵌套多个li,为ul注册事件对象，点击里面的li,输出this为ul,输出e.target为li

![image-20220911101507223](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911101507223.png)

了解跟 this 有个非常相似的属性 e.currentTarget  ie678不认识

5.2阻止默认行为(事件)  让链接不跳转,按钮不生效    

 **e.preventDefault();方法**            e.returnValue;属性(低版本)      return false;(限于传统)

5.3阻止事件冒泡:开始时由最具体的元素接收，然后逐级向上传播到到 DOM 最顶层节点。

案例中:为docoument,father,son都注册了冒泡点击事件，要是想点击son就弹出son这一个警示框，就要用阻止冒泡

 **e.stopPropagation();**方法         e.cancelBubble = true; 属性(低版本)



##### 6.事件委托(事件委派)

6.1事件委托的原理

**不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。**

以上案例：给 ul 注册点击事件，然后利用**事件对象的 target** 来找到当前点击的 li，**因为点击 li，事件会冒泡到 ul 上，** ul 有注册事件，就会触发事件监听器。

6.2事件委托的作用

我们只操作了一次 DOM ，提高了程序的性能。

案例:var ul = document.querySelector('ul');

​    ul.addEventListener('click', function(e) {

​      // alert('知否知否，点我应有弹框在手！');

​      // e.target 这个可以得到我们点击的对象

​      e.target.style.backgroundColor = 'pink'; }



##### 7.常用的鼠标事件

7.1禁止鼠标右键菜单**contextmenu**                     

主要控制应该何时显示上下文菜单，主要用于程序员取消默认的上下文菜单，配合**e.preventDefault();**使用

7.2.禁止鼠标选中   **selectstart**        配合**e.preventDefault();**使用



7.3鼠标事件对象

event对象代表事件的状态，跟事件相关的一系列信息的集合。现阶段我们主要是用鼠标事件对象 MouseEvent 和键盘事件对象 KeyboardEvent。

![image-20220911130749756](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911130749756.png)



##### 8.常用的键盘事件

![image-20220911133006526](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911133006526.png)

keydown和keypress中同时按下非功能键先执行keydown,keyup不区分大小写，按大写  keypress能区别大小写

8.2 键盘事件对象

![image-20220911133556388](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911133556388.png)

​           **keyCode属性能区分大小写**，返回不同的ASCII值



京东搜索案例中:触发事件用keyup，键盘抬起时才触发，否则用keydown,和keypress会把s值写进去

京东物流案例:注意： keydown 和 keypress 在文本框里面的特点： **他们两个事件触发的时候，文字还没有落入文本框中。**

keyup事件触发的时候， 文字已经落入文本框里面了,用keypress删除键不能用





#### 四.BOM(游览器对象模型)

##### 1.BOM

1.1特点:     1.把「浏览器」当做一个「对象」来看待,                     2.BOM 的顶级对象是 window,

​                   3.BOM 学习的是浏览器窗口交互的一些对象                4.BOM 是浏览器厂商在各自浏览器上定义的，兼容性较差

1.2BOM 的构成

window 对象是浏览器的顶级对象，它具有双重角色。

它是 JS 访问浏览器窗口的一个接口。

它是一个全局对象。**定义在全局作用域中的变量、函数都会变成 window 对象的属性和方法**。在调用的时候可以**省略 window**，前面学习的对话框都属于 window 对象方法，如 alert()、prompt() 等。

注意：window下的一个特殊属性 window.name



##### 2.window 对象的常见事件

**2.1 窗口加载事件**:  当文档内容完全加载完成会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。

传统:window.onload = function() {}    或者    最新:**window.**addEventListener("**load**",function(){});

注意：有了 window.onload 就可以把 JS 代码写到页面元素的上方，因为 onload 是等页面内容全部加载完毕，再去执行处理函数。



document.addEventListener('**DOMContentLoaded**',function(){})   

注意:1.**仅当DOM加载完成**，不包括**样式表，图片，flash**等等。

2.Ie9以上才支持：（适应情况）如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。

##### 2.2 调整窗口大小事件

传统:window.onresize = function(){}               最新:**window.**addEventListener("**resize**",function(){});

注意:1.只要窗口大小发生像素变化，就会触发这个事件。

​        2.我们经常利用这个事件完成响应式布局。 window.**innerWidth** 当前屏幕的宽度



##### 2.3定时器

2.3.1window**.setTimeout**(调用函数, [延迟的毫秒数]);          方法用于设置一个定时器，该定时器在定**时器到期后执行调用函数。**

注意:**window 可以省略**   这个调用函数可以直接写函数，或者写函数名或者采取字符串‘函数名()'三种形式。

2.3.2回调函数: setTimeout()  这个调用函数我们也称为回调函数 callback

以前我们讲的   element.onclick = function(){}   或者  element.addEventListener(“click”, fn);   里面的 函数也是回调函数。



##### 2.4停止 setTimeout() 定时器

window.**clearTimeout**(timeoutID)  括号里是定时器的标识符，取消先前通过调用 setTimeout() 建立的定时器。



##### 2.5  setInterval() 定时器

window.**setInterval**(回调函数, [间隔的毫秒数]); **重复调用一个函数，每隔这个时间,**就去调用一次回调函数。

倒计时案例:  var nowTime = +new Date(); // 返回的是当前时间总的毫秒数       使用setInterval() 定时器设置每隔一秒调用倒计时函数

第一次执行也是间隔毫秒数，因此刚刷新页面会有空白最好采取封装函数的方式， 这样可以先调用一次这个函数，防止刚开始刷新页面有空白问题

##### 2.6停止 setInterval() 定时器

 window.**clearInterval**(intervalID);括号里是定时器的标识符，取消先前通过调用 setInterval()建立的定时器。



#### 3.this指向问题

this的指向在函数定义的时候是确定不了的，只有**函数执行的时候才能确定this到底指向谁**，一般情况下this的最终指向的是那个调用它的对象

 // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）  **window.**fn(); window省略了

//  2. 方法调用中谁调用this指向谁

//  3.构造函数中this指向构造函数的实例



#### 4.JS执行机制

##### 4.1 JS 是单线程

所有任务需要排队，前一个任务结束，才会执行后一个任务。这样所导致的问题是： **如果 JS 执行的时间过长**，这样就会造成页面的**渲染不连贯，导致页面渲染加载阻塞**的感觉。

##### 4.2 同步和异步(为了解决这个问题，利用多核 CPU 的计算能力，允许 JavaScript 脚本创建多个线程。于是，JS 中出现了同步和异步。)

同步:前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。

异步:同时可以做多个任务

他们的本质区别： **这条流水线上各个流程的执行顺序不同。**

案例:打印1,settimeout定时器设置2秒后打印2，打印3   输出结果是132

##### 4.3异步任务

同步任务都在主线程上执行，形成一个执行栈。

**JS 的异步是通过回调函数实现的。**

异步任务有以下三种类型: 1.普通事件，如 click,resize 等  2.资源加载，如 load,error 等    3定时器，包括 setInterval、setTimeout 

异步任务相关回调函数添加到任务队列中（任务队列也称为消息队列）。

##### 4.4 JS 执行机制

1.先执行执行栈中的同步任务。

2.异步任务（回调函数）放入任务队列中。

3.一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行.执行栈时不时会看任务队列里是否有异步任务，如果有，则放入执行栈执行

![image-20220911201017846](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911201017846.png)

由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为**事件循环**（ event loop）。



#### 5.location 对象

**5.1简介:**window 对象给我们提供了一个 location 属性用于**获取或设置窗体的 URL**，并且可以用于解析 URL 。 因为这个属性返回的是一个对象，所以我们将这个属性也称为 location 对象。

##### 5.2URL

互联网上标准资源的地址。互联网上的每个文件都有一个唯一的 URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。

URL 的一般语法格式为： protocol://host[:port]/path/[?query]#fragment

​                                              http://www.itcast.cn/index.html?name=andy&age=18#link

![image-20220911201358502](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911201358502.png)

##### 5.3 location 对象的属性

![image-20220911201640329](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911201640329.png)

​                                                                    **href                 search**



**获取 URL 参数数据案例:**在登陆页面from表单里action代表要提交数据的网址，文本框里的name必须要写，提交到index页面后，用location.sourse属性获取参数，得到?uname=andy；用String对象方法subtar(从第几个开始取，取几个)把？去掉，然后再用spilt(’分隔符‘)方法将name和andy存储到一个数组里，再把数组的第二个元素拿出来即可。

##### 5.4location 对象方法

![image-20220911204949687](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911204949687.png)

location**.assign()**方法**记录浏览历史，所以可以实现后退功能 **  location.assign('http://www.itcast.cn');中间有**参数**

location.replace方法不记录浏览历史无法实现后退功能

#### 6.navigator 对象

包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。

例如游览器逛京东时能根据手机，电脑设备不同进入不同的网页，

截取代码navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|....))   window.location.href = "";     //手机

#### 7.history 对象

简介:window 对象给我们提供了一个 history 对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的 URL。

后退/前进网页

![image-20220911210509659](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220911210509659.png)



#### 五:PC 端网页特效

##### 5.1offset 概述

offset 翻译过来就是偏移量， 我们使用 offset 系列相关属性可以**动态的**得到该元素的位置（偏移）、大小等。 

获得元素距离带有定位父元素的位置 获得元素自身的大小（宽度高度） 注意： 返回的数值都不带单位

![image-20220912093737369](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220912093737369.png)

   它以带有**定位的父亲**为准，如果么有父亲或者父亲没有定位 则以 body 为准

​    console.log(son.offsetParent); // 返回带有定位的父亲 否则返回的是body

​    console.log(son.parentNode); // 返回父亲 是最近一级的父亲 亲爸爸 不管父亲有没有定位

##### 5.2 offset 与 style 区别

**offset** 1.可以得到**任意样式表**中的样式值          2.获得的数值是没有单位的                  3.offsetWidth 包含padding+border+width                                              4.offsetWidth 等属性是只读属性，**只能获取不能赋值**所以，我们想要获取元素大小位置，用offset更合适

**style **  1.style 只能得到**行内样式表**中的样式值              2.style.width 获得的是带有单位的字符串          

​            3.style.width 获得不包含padding和border 的值              

​            4.style.width 是**可读写属性，可以获取也可以赋值**，所以我们想要给元素更改值，则需要用style改变



拖动模拟框案例中: 1**.鼠标的坐标 减去 鼠标在盒子内的坐标， 才是模态框真正的位置。**将此值赋值给login.style.top//left

2.鼠标按下移动才触发，用嵌套结构



京东放大镜案例:

移动黄色遮挡层，大图片跟随移动功能。求大图片的移动距离公式

##### 5.3元素可视区 client 系列

简介:client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。通过 client 系列的相关属性可以动态的得到该元素的边框大小、元素大小等。

![image-20220912141114207](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220912141114207.png)

和offsetWidth 最大的区别就是 **不包含边框**



**立即执行函数:** 不需要调用，立马能够自己执行的函数,

最大的作用就是独立创建了一个作用域, 里面所有的变量都是局部变量 不会有命名冲突的情况

写法 也可以传递参数进来    // 1.**(function() {})()**   或者  2. **(function(){}());**

 (function(a, b) {                                                                        (function sum(a, b) {             //可以有名字sum

 console.log(a + b);                                                                      console.log(a + b);

  var num = 10;                                                                             var num = 10; // 局部变量

  })(1, 2); // 第二个小括号可以看做是调用函数                          }(2, 3));



##### 5.4 元素滚动 scroll 系列

使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。

  ![image-20220912155754508](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220912155754508.png)

   5.4.1 页面被卷去的头部

  如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 on**scroll** 事件。



淘宝滚动条案例:

需要用到页面滚动事件 scroll  因为是页面滚动，所以事件源是 document

滚动到某个位置，就是判断页面被卷去的上部值。

**页面被卷去的头部：可以通过window.pageYOffset 获得  如果是被卷去的左侧 window.pageXOffset**

注意，元素被卷去的头部是 element.scrollTop  , 如果是页面被卷去的头部 则是 window.pageYOffset

其实这个值 可以通过盒子的 offsetTop 可以得到，如果大于等于这个值，就可以让盒子固定定位了

**window.scroll(0,0)**

页面被卷去的头部，有兼容性问题，因此被卷去的头部通常有如下几种写法

1. 声明了 DTD，使用 document.documentElement.scrollTop        2. 未声明 DTD，使用  document.body.scrollTop

##### 三大系列总结

![image-20220912164703117](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220912164703117.png)

1.offset系列 经常用于**获得元素位置**    offsetLeft  offset                    2.Topclient 经常用于**获取元素大小**  clientWidth  clientHeight

3.scroll 经常用于**获取滚动距离**  scrollTop  scrollLeft                         4.注意页面滚动的距离通过 window.pageXOffset



##### mouseenter 和mouseover的区别

**mouseover鼠标经过自身盒子会触发，经过子盒子还会触发**。 **mouseenter  只会经过自身盒子触发**

之所以这样，就是因为**mouseenter不会冒泡**,跟 mouseenter搭配鼠标离开mouseleave同样不会冒泡



##### 4.动画原理

 4.1核心原理：通过**定时器 setInterval()** 不断移动盒子位置。**盒子必须要加定位**

​         实现步骤：1. 获得盒子当前位置                2. 让盒子在当前位置加上1个移动距离            3. 利用定时器不断重复这个操作    

​                   4.加一个结束定时器的条件         5. 注意此元素需要添加定位，才能使用element.style.left



4.2 动画函数简单封装

​              注意函数需要传递2个参数，动画对象和移动到的距离

​             function animate(obj(目标对象), target(目标位置)) { var timer = setInterval(function(){  .........................       }}

4.3 动画函数给不同元素记录不同定时器

​             **obj.timer** = setInterval(function() { ....................}

​                // 当我们不断的点击按钮，这个元素的速度会越来越快，因为开启了太多的定时器

​               // 解决方案就是 让我们元素只有一个定时器执行

​              // 先清除以前的定时器，只保留当前的一个定时器执行

4.4 缓动效果原理

​            缓动动画就是让元素运动速度有所变化，最常见的是让速度慢慢停下来

​            思路：1.    让盒子每次移动的距离慢慢变小，速度就会慢慢落下来。

​             核心算法： **(目标值 - 现在的位置 )  / 10** 做为每次移动的距离,   步长停止的条件是:让当前盒子位置等于目标位置就停止定时器  注意步长**值需要取整**,否则可能达不到预期值就停下

4.5 动画函数多个目标值之间移动    

​               可以让动画函数从 800 移动到 500。当点击按钮时候，判断步长是正值还是负值如果是正值，则步长往大了取整如果是负值，则步长向小了取整

4.6 动画函数添加回调函数

​              原理：函数可以作为一个参数。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后，再执行传进去的这个函数，这个过程就叫做回调。

​              回调函数写的位置：定时器结束的位置。

4.7 动画函数封装到单独JS文件里面

​               因为以后经常使用这个动画函数，可以单独封装到一个JS文件里面，使用的时候引用这个JS文件即可。单独新建一个JS文件。HTML文件引入 JS 文件。



轮播图案例中:

1.动态生成小圆圈    小圆圈的个数要与图片数量一致，第一个小圆圈设置current类

2.小圆圈的排他思想  e.target

3.点击小圆圈滚动图片 在创建圆圈时给每个小圆圈设置自定义属性以获得索引号,点击某个圆圈移动索引号乘以宽度的距离，同时利用排他思想将点击的小圆圈变化，注意num的值跟自定义属性index的值相关联

4.点击右侧按钮一次，就让图片滚动一张。  声明一个变量num,点击一次,自增1,num的值跟index相关联，

5.克隆第一张图片 为了轮播图连贯，在创建晕圈后**深复制**节点，在点击到最后一张复制的图片时，判断条件，设置对应的小圆圈亮点为0，设置ul的left,以及num也为0；

7.自动播放功能   设置setInterval() 定时器，调用方法 **arrow_r.click();**自动点击右键按钮实现,在经过事件轮播图标签下设置清除此定时器，然后将timer的值设为null,以释放内存资源。因此不要忘了将此定时器存储进入一个变量中，在离开事件标签轮播图重新开启。



##### 5.节流阀

节流阀目的：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。

核心实现思路：利用回调函数，添加一个变量来控制，锁住函数和解锁函数。 

开始设置一个变量 var flag = true;If(flag) {flag = false; do something}关闭水龙头利用回调函数 动画执行完毕， flag = true ,打开水龙头

**callback && callback();**利用短路运算实现动画封装函数的简洁写法



返回顶部案例: 滚动窗口至文档中的特定位置。**window.scroll(x, y)** ;**里面的x和y 不跟单位，直接写数字**

精斗云案例:如果点击了某个小li， 就把li当前的位置存储起来，做为筋斗云的起始位置



#### 六:移动端网络特效

##### 1.触屏事件

简介:移动端浏览器兼容性较好，**不需要考虑以前 JS 的兼容性问题**，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如触屏事件 touch（也称触摸事件）

![image-20220913110646890](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220913110646890.png)

#####  2.触摸事件对象（TouchEvent）

![image-20220913111227401](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220913111227401.png)

如果侦听的是一个DOM元素，touches, targetTouches他们两个是一样的

因为我们一般都是触摸元素 所以最经常使用的是 **targetTouches**

##### 3.移动端拖动元素

拖动元素需要当前手指的坐标值,我们可以使用targetTouches[0] 里面的pageX 和 pageY 

手指移动中，计算出手指移动的距离。然后用盒子原来的位置 + 手指移动的距离

拖动元素三步曲：（1） 触摸元素 touchstart：  获取手指初始坐标，同时获得盒子原来的位置

​                               （2） 移动手指 touchmove：  计算手指的滑动距离，并且移动盒子

​                               （3） 离开手指 touchend:

 //  获取手指初始坐标   startX = **e.targetTouches[0]**.pageX;

注意： 手指移动也会触发滚动屏幕所以这里要阻止默认的屏幕滚动 e.preventDefault();



移动端轮播图案例中:由于js是引入式，写在html,body文件上方，由于js的从上到下逐行解释的规则，不执行window的load注册时间是打死都不会获取到元素的。



classList属性是HTML5新增的一个属性，返回元素的类名。但是ie10以上版本支持。该属性用于在元素中添加，移除及切换 CSS 类。返回伪数组，有以下方法

添加类：element.classList.add（’类名’）；追加类名,不会覆盖,不要加小点点         移除类：element.classList.remove（’类名’）;

切换类：element.classList.**toggle**(’类名’）；如果有这个类，就删除这个类，如果没有就加上



##### 4.click 延时解决方案

移动端 click 事件会有 300ms 的延时，原因是移动端屏幕双击会缩放(double tap to zoom) 页面。

**解决方案：**1. 禁用缩放。 浏览器禁用默认的双击缩放行为并且去掉 300ms 的点击延迟。

​                   <.meta name="viewport" content="user-scalable=no">

2. 利用touch事件自己封装这个事件解决 300ms 延迟。

原理就是：1. 当我们手指触摸屏幕，记录当前触摸时间2. 当我们手指离开屏幕， 用离开的时间减去触摸的时间3. 如果时间小于150ms，并且没有滑动过屏幕， 那么我们就定义为点击

3. 使用插件。 fastclick 插件解决 300ms 延迟。

   

##### 5.插件的使用

移动端要求的是快速开发，所以我们经常会借助于一些插件来帮我完成操作，那么什么是插件呢？JS 插件是 js 文件，它遵循一定规范编写，方便程序展示效果，拥有特定功能且方便调用。如轮播图和瀑布流插件。特点：它一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

5.1fastclick 插件

1. 引入 js 插件文件。2. 按照规定语法使用                fastclick 插件解决 300ms 延迟。 使用延时

   GitHub官网地址： https://github.com/ftlabs/fastclick

5.2 Swiper 插件的使用

不要更改里面的结构和类名

5.3插件的使用总结

1.确认插件实现的功能                      2.去官网查看使用说明                                3.下载插件                                                                                                               4.打开demo实例文件，查看需要引入的相关文件，并且引入                    5.复制demo实例文件中的结构html，样式css以及js代码

##### 6.框架的使用

框架，顾名思义就是一套架构，它会基于自身的特点向用户提供一套较为完整的解决方案。框架的控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。

插件一般是为了解决某个问题而专门存在，其功能单一，并且比较小。

前端常用的框架有 Bootstrap、Vue、Angular、React 等。既能开发PC端，也能开发移动端前端常用的移动端插件有 swiper、superslide、iscroll等。

框架： 大而全，一整套解决方案

插件： 小而专一，某个功能的解决方案



#### 七.本地存储

##### 1.本地存储特性

1、数据存储在**用户浏览器**中                                                                 2、设置、读取方便、**甚至页面刷新不丢失数据**                                                                                         3、容量较大**，sessionStorage约5M、localStorage约20M**           4、只能存储**字符串**，可以将对象JSON.stringify() 编码后存储

##### 2.window.sessionStorage

1、生命周期为关闭浏览器窗口           2、在同一个窗口(页面)下数据可以共享           3.   以键值对的形式存储使用

存储数据：sessionStorage.setItem(key, value)       sessionStorage.setItem(**'uname'**, value);

获取数据：sessionStorage.getItem(key)

删除数据：sessionStorage.removeItem(key)

删除所有数据：sessionStorage.clear()

##### 3.window.localStorage

1、声明周期永久生效，除非手动删除 否则关闭页面也会存在                                   2、可以多窗口（页面）共享（同一浏览器可以共享）3.   以键值对的形式存储使用

存储数据：localStorage.setItem(key, value)     

获取数据：localStorage.getItem(key)

删除数据：localStorage.removeItem(key)

删除所有数据：localStorage.clear()



记住用户名案例：

把数据存起来，用到本地存储关闭页面，也可以显示用户名，所以用到localStorage打开页面，先判断是否有这个用户名，如果有，就在表单里面显示用户名，并且勾选复选框当复选框发生改变的时候 change事件如果勾选，就存储，否则就移除
