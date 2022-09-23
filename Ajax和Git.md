### 一.服务器的基本概念与初识Ajax

#### 1.客户端与服务器

#### 2.URL

##### 2.1简介

统一资源定位符，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。

##### 2.2 URL地址的组成部分

一般由三部组成：① 客户端与服务器之间的通信协议② 存有该资源的服务器名称③ 资源在服务器上具体的存放位置

![image-20220914170324958](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220914170324958.png)

#### 3.客户端与服务器的通信过程

请求-处理-响应

#### 4.服务器对外提供了哪些资源

##### 4.1数据是网页的灵魂

##### 4.2网页中如何请求数据

如果要在网页中请求服务器上的数据资源，则需要用到 **XMLHttpRequest** 对象。

最简单的用法 var xhrObj = new XMLHttpRequest()

##### 4.3资源的请求方式

客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别为 get 和 post 请求。

get 请求通常用于获取服务端资源（向服务器要资源）      例如：根据 URL 地址，从服务器获取 HTML 文件、css 文件、js文件、图片文件、数据资源等

post 请求通常用于向服务器提交数据（往服务器发送资源）      例如：登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

#### 5.AJAX

##### 5.1.XML可扩展标记语言，被设计用来传输和存储数据，里面都是自定义标签

通俗的理解：在网页中利用 XMLHttpRequest 对象和服务器进行数据交互的方式，就是Ajax。

Ajax能让我们轻松实现网页与服务器之间的**数据交互**。效果大多配合懒加载

##### 5.2.优缺点  

优:无需刷新页面就能与服务器发送请求(初衷),允许用户事件来更新部分页面

 缺:没有游览历史，不能回退，SEO不友好，存在跨域问题

#### 6.jQuery中的Ajax

6.1简介

浏览器中提供的 XMLHttpRequest 用法比较复杂，所以 jQuery 对 XMLHttpRequest 进行了封装，提供了一系列 Ajax 相关的函数，极大地降低了 Ajax 的使用难度。

jQuery 中发起 Ajax 请求最常用的三个方法如下： $.get()            $.post()             $.ajax()



##### 6.2 $.get()函数的语法

6.2.1 简介:jQuery 中 $.get() 函数的功能单一，专门用来发起 get 请求，从而将服务器上的资源请求到客户端来进行使用。

6.2.2 $.get() 函数的语法如下：   $.get(**url**, [data], [callback])                                 

data参数类型为Object,表示资源期间携带的参数                  calllback参数类型是function,表示请求成功时的回调函数

案例: $.get()发起不带参数的请求

$.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {    console.log(res) // 这里的 res 是服务器返回的数据})   status: 200代表获取成功

案例: $.get()发起带参数的请求

 $.get('http://www.liulongbin.top:3006/api/getbooks',{bookname: "西游记"},function(res){ console.log(res); })

##### 6.3 $.post()函数的语法

6.3.1简介:jQuery 中 $.post() 函数的功能单一，专门用来发起 post 请求，从而向服务器提交数据。

6.3.2$.post() 函数的语法如下：$.post(url, [data], [callback])

data参数类型为Object,代表要提交的数据

案例:$.post('http://www.liulongbin.top:3006/api/addbook', **{ bookname: '水浒传1', author: '施耐庵', publisher: '天津图书出版社' }**, function (res) {   console.log(res) })

##### 6.4$.ajax()函数的语法

相比于 $.get() 和 $.post() 函数，jQuery 中提供的 $.ajax() 函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。

$.ajax() 函数的基本语法如下：

$.ajax({   **type: '   ',** // 请求的方式，例如 GET 或 POST(建议大写)   **url: '  ',**  // 请求的 URL 地址   

​           **data: { }**,// 这次请求要携带的数据，可省略                    **success: function(res) { }** // 请求成功之后的回调函数})



#### 7.接口

##### 7.1接口的概念

用 Ajax 请求数据时，被请求的 URL 地址，就叫做数据接口（简称接口）。同时，每个接口必须有**请求方式**(GET/POST)。

例如GET/POST请求的url地址

##### 7.2 分析接口的请求过程

数据载体包裹ajax             基于请求-处理-响应的过程

##### 7.3 接口测试工具

为了验证接口能否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测。

好处：接口测试工具能让我们在不写任何代码的情况下，对接口进行调用和测试。

注意:提交数据选择get时是parama    post时是body-x.www.....

##### 7.4接口文档

接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：

 接口名称：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。 

接口URL：接口的调用地址。 

调用方式：接口的调用方式，如 GET 或 POST。 

参数格式：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这4项内容。 

响应格式：接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容。 status,msg,data

返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。{    }

#### 8.案例

图书案例:**1.获取图书列表，加载现有的图书**，利用$.get方法向服务器发送请求后，利用res打印查看返回的信息；得到数据后，创建一个数组，遍历返回的参数，JQuery中提供了**each方法**,

语法1:$("div").each(function (index, domEle) { xxx; }）

语法2:$.each(object，function (index, element) { xxx; }）

返回的参数是一组对象，里面有许多属性，因此用第二种方法进行遍历，push进创建的数组， arr.push('<tr><td>' + item.id + '</td>+.....+<td><a href="javascript:;" class="del" data-id="' + item.id + '">删除</a></td></tr>'),然后在父元素append操作，$('#tb').empty().append(arr.join('')) ;//**empty方法**清除子节点，**append方法**在父元素最后添加节点，相当于appendChild

**2.删除图书**，删除图书先拿到图书的id，id是图书的唯一标识符，这里的id可以在创建a时的自定义属性data-index获取， var id=$(this).**attr**('data-id')。注意:不能直接给a链接注册事件，后期append上去的元素无法通过$获取的到，把原来加给子元素身上的事件绑定在父元素身上，就是把事件**委派**给父元素。代理，为动态添加的元素绑定点击事件， $('#tb').on('click',**'.del'**,function(e){}，注意事件处理完后要重新刷新页面，获取图书，这里将模块1封装进一个函数里

**3.添加图书**  注意: var bookname=$('#iptBookname').val().**trim()**;//去除字符串两端空格



聊天机器人案例:**1.获取聊天框内容发送** 注意:获取的时候注意判断是不是空字符串，同上面一样， resetui()方法 //向聊天内容发送后，让滚动条重置到最低端，添加内容：

**2.发送请求获取返回信息**  注意 //先看返回的消息数据有没有status在做判断，不要瞎写，这里返回的值没有status，有message=某字符串，拿这个属性做判断，返回的文本内容在res.data.info.text，创建一个变量存储起来，

**3.将返回的信息转化为语音**,在html主界面添加audio标签，设置autoplay自动播放属性，url留空，别忘了隐藏标签在获取到返回的参数有message，status，voiceUrl，其中语音内容存储在voiceUrl中，然后通过**attr**(' 属性名','属性值 ')的方法添加进去

**4.按下键盘回车键发消息**  为输入框标签注册键盘事件，为keyup,用键盘事件属性keyCode方法判断是否按下了回车键，其中回车键的ascoal码是13，   **$('.input_sub').click();**按下回车键相当于点击了发送按钮，二，三模块注意text参数在函数间的传递



### 二:form表单与模板引擎

#### 1.form表单的基本使用

##### 1.1 什么是表单

表单在网页中主要负责数据采集功能。HTML中的<form>标签，就是用于采集用户输入的信息，并通过<form>标签的提交操作，把采集到的信息提交到服务器端进行处理。

##### 1.2 表单的组成部分

表单标签          表单域              表单按钮

##### 1.3 <form>标签的属性

| **属性** | **值**                                                       | **描述**                                  |
| -------- | ------------------------------------------------------------ | ----------------------------------------- |
| action   | URL地址                                                      | 规定当提交表单时，向何处发送表单数据      |
| method   | get或post                                                    | 规定以何种方式把表单数据提交到 action URL |
| enctype  | application/x-www-form-urlencodedmultipart/form-datatext/plain | 规定在发送表单数据之前如何对其进行编码    |
| target   | _blank_self_parent_top*framename*                            | 规定在何处打开 action URL                 |

1.3.1 target 属性用来规定在何处打开 action URL。 target 的值是 __self,_ 相同的框架中打开，_blank在新建网页打开，俩最常用

1.3.2 method默认值是get        ?是来分割url和提交数据,数据之间用&分割       post方式更安全，在url上不会显示提交数据

注意：get 方式适合用来提交少量的、简单的数据。post 方式适合用来提交**大量的、复杂的、或包含文件上传**的数据。在实际开发中<form> 表单的 **post** 提交方式用的最多，很少用 get。例如登录、注册、添加数据等表单操作，都需要使用 post 方式来提交表单。

1.3.3 enctype 属性用来规定在发送表单数据之前如何对数据进行编码。它的可选值有三个，默认情况下，enctype 的值为 application/x-www-form-urlencoded，表示在发送前编码所有的字符。 

multipart/form-data不对字符编码。**在使用包含文件上传控件的表单时，必须使用该值。**

text/plain  空格转换为 “+” 加号，但不对特殊字符编码。（很少用/）

##### 1.4 表单的同步提交及缺点

1.4.1通过点击 submit 按钮，触发表单提交的操作，从而使页面跳转到 action URL 的行为叫做表单的同步提交。

1.4.2表单同步提交的缺点

1.整个页面会发生跳转，跳转到 action URL 所指向的地址，用户体验很差。    2.页面之前的状态和数据会丢失。

1.4.3如何解决表单同步提交的缺点

**表单只负责采集数据，Ajax 负责将数据提交到服务器。**

#### 2.通过Ajax提交表单数据

##### 2.1 监听表单提交事件

$('#form1').submit(function(e) {   })                 $('#form1').on('submit', function(e){  })

##### 2.2 阻止表单默认提交行为

可以调用事件对象的 **event.preventDefault()** 函数,阻止默认行为

##### 2.3 快速获取表单中的数据

为了简化表单中数据的获取操作，jQuery 提供了$(selector).**serialize()** 可以一次性获取到表单中的所有的数据

调用的结果：username=用户名的值&password=密码的值,这里的属性名是name里的值，**必须为每个表单元素添加 name 属性**！

#### 3.案例 - 评论列表

操作方法基本和图书列表相同，不过在最后发表评论后将form表单里的内容清空时，可以用$('#f1')[0].reset();可以剩下很多时间，不用一个一个去清空，这里是将jquery对象转化为dom对象，因为reset方法只适用于DOM对象

#### 4.模板引擎的基本概念

##### 4.1抛出问题

以上案例:上述代码是通过字符串拼接的形式，来渲染UI结构。如果UI结构比较复杂，则拼接字符串的时候需要格外注意引号之前的嵌套。且一旦需求发生变化，修改起来也非常麻烦。

##### 4.2什么是模板引擎

顾名思义，它可以根据程序员指定的**模板结构和数据**，**自动**生成一个完整的HTML页面。

##### 4.3 模板引擎的好处

减少了字符串的拼接操作               使代码结构更清晰             使代码更易于阅读与维护

#### 5.art-template模板引擎

##### 5.1 art-template简介

art-template 是一个简约、超快的模板引擎。中文官网首页为 http://aui.github.io/art-template/zh-cn/index.html

##### 5.2 art-template的安装

##### 5.3art-template的使用

1.导入 art-template          

2.定义数据           var data = { name: 'zs', age: 20, hobby: ['吃饭', '睡觉', '写代码'], regTime: new Date() }

3.定义模板            模板的 HTML 结构，必须定义到 script 中如<script type="text/html" id="tpl-user"> {{name}}占位符       <h1>{{name}}   ------   {{age}}</h1>

4.调用 template 函数          var htmlStr = template('tpl-user', data//res(数据))     

5.渲染HTML结构     $('#container').html(**htmlStr**)

##### 5.4 art-template标准语法

art-template 提供了 {{ }} 这种语法格式，在 {{ }} 内可以进行变量输出，或循环数组等操作，这种 {{ }} 语法在 art-template 中被称为标准语法。

5.4.2标准语法 - 输出

{{value}}      {{obj.key}}           {{obj['key']}}           {{a ? b : c}}           {{a || b}}           {{a + b}}

5.4.3标准语法 – 原文输出

{{@ value }}  如果要输出的 value 值中，包含了 HTML 标签结构，则需要使用原文输出语法，才能保证 HTML 标签被正常渲染。

5.4.4标准语法 – 条件输出

如果要实现条件输出，则可以在 {{ }} 中使用 if … else if … /if 的方式，进行按需输出

{{if value}} 按需输出的内容 {{/if}}               {{if v1}} 按需输出的内容 {{else if v2}} 按需输出的内容 {{/if}}

5.4.5标准语法 – 循环输出

如果要实现循环输出，则可以在 {{ }} 内，通过 each 语法循环数组，当前循环的索引使用 $index 进行访问，当前的循环项使用 $value 进行访问。

{{each arr}}           {{$index}} {{$value}}     {{/each}}

5.4.6标准语法 – 过滤器

{{value | filterName}}   过滤器语法类似管道操作符，它的上一个输出作为下一个输入。注意:过滤器最后一定要 return 一个值

定义过滤器的基本语法如下：

template.defaults.imports.filterName = function(value){/*return处理的结果*/}    注意*号

#### 6.案例-新闻列表

**1.刷新新闻列表** 这里利用art-template渲染引擎美化界面，1.引入art-template渲染  2.定义数据，这里的数据就是通过$.get返回的数据。3.定义模板 <script type="text/html" id="tpl-user"> 中间的内容把上面的内容粘贴下来，在做参数上的修改，同时由于res返回的data有多条数据，别忘了加上{{each data}} 内容{{/each}}遍历里面的data  </script>> 4.调用template 函数  var htmlStr = template('tpl-user', res) ,这里的res代表数据，在$.get方法传递的回调函数   5.渲染HTML结构     $(选择器).html(**htmlStr**)

注意:图片返回的是url图片地址，再次之前还要加上根地址才能完整显示图片

​    在span标签中，由于tags数量不是固定的，因此在传res到渲染引擎之前可以把res.data[i].tags通过split方法转化为数组，在同此前data一样，在span标签位置也放 {{each $value.tags}}<s.pan>{{$value}}</span> {{/each}},**注意each旁边的$value代表data源数组，表示data.tags,而中间的$value代表tags里面的索引值，这一点特别要分清楚**

2.过滤器的使用    <s.pan>{{$value.time | filterName}}</span>

template.defaults.imports.filterName = function(value)  {  var timer=new Date(time)   return timer.toLocaleString(); }

#### 7.模板引擎的实现原理

##### 7.1 正则与字符串操作

exec() 函数用于检索字符串中的正则表达式的匹配。  pattern.**exec**(str)   pattern是正则表达式，str是被检测的字符串

输出的结果示例["o", index: 4, input: "hello", groups: undefined]

test() 函数也可以用来检测，语法同exec()一样，不过它返回的结果是布尔型

##### 7.2分组

正则表达式中 ( ) 包起来的内容表示一个分组，可以通过分组来提取自己想要的内容，

var pattern = /{{**(**[a-zA-Z]+**)**}}/

var patternResult = pattern.exec(str)

输出patternResult结果为数组["{{name}}", "name", index: 7, input: "<div>我是{{name}}</div>", groups: undefined]

##### 7.3 replace函数

 var str2 = "Today is fine day,today is fine day !!!"

console.log(str2.replace("today","tomorrow"));  //只能替换第一个today
console.log(str2.replace(/today/gi,"tomorrow")); //这里用到了正则，且为“全局匹配”模式，才能替换所有的today

g代表全局匹配模式 i代表忽略大小写

利用分组str = str.replace(patternResult[0], patternResult[1])

多次replace  和while循环

### 三.Ajax加强

#### 1.XMLHttpRequest的基本使用

##### 1.1 什么XMLHttpRequest

XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它可以请求服务器上的**数据资源**。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

##### 1.2 使用xhr发起GET请求

 var xhr = new XMLHttpRequest()                                                           // 1. 创建 XHR 对象

xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')     // 2. 调用 open 函数

xhr.send()                                                                                                    // 3. 调用 send 函数

xhr.onreadystatechange = function () {                                                  // 4. 监听 onreadystatechange 事件

 if (xhr.readyState === 4 && xhr.status === 200) {                              // 5.获取服务器响应的数据 

console.log(xhr.**responseText**)  }  }  获得字符串形式的响应数据  

注意:判断条件里的status是固定写法，跟返回数据的status不是同一个

##### 1.3.了解xhr对象的readyState属性

对用于xhr发起GET请求的5个步骤

##### 1.4 使用xhr发起带参数的GET请求

xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks**?id=1**')   在 URL 地址后面拼接的参数，叫做**查询字符串**。

##### 1.5 查询字符串

定义：查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。

格式：将英文的 ? 放在URL 的末尾，然后再加上 **参数＝值** ，想加上多个参数的话，使用 & 符号进行分隔。以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

无论使用 $.ajax()，还是使用 $.get()，又或者直接使用 xhr 对象发起 GET 请求，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。

##### 1.6 URL编码与解码

URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。

如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。

URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。URL编码原则的通俗理解：使用英文字符去表示非英文字符。中文一个字有三组百分号

对URL进行编码与解码:        encodeURI()  编码的函数          decodeURI()  解码的函数

由于浏览器会自动对 URL 地址进行编码操作，因此，大多数情况下，程序员不需要关心 URL 地址的编码与解码操作。

##### 1.7 使用xhr发起POST请求

  var xhr = new XMLHttpRequest()                                                                                              // 1. 创建 xhr 对象

  xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')                                    // 2. 调用 open 函数

  xhr.**setRequestHeader**('**Content-Type**', **'application/x-www-form-urlencoded**')   // 3. 设置Content-Type属性函数

  xhr.send('bookname=水浒传&author=施耐庵&publisher=上海图书出版社')                 // 4. 调用 send 函数

  xhr.onreadystatechange = function () {                                                                                  // 5. 监听事件

   if (xhr.readyState === 4 && xhr.status === 200) {console.log(xhr.responseText)  }  }    //6.获得字符串形式的响应数据                                                               

#### 2.数据交换格式

##### 2.1 什么是数据交换格式

数据交换格式，就是**服务器端与客户端之间进行数据传输与交换的格式**。

前端领域，经常提及的两种数据交换格式分别是 XML 和 **JSON**。

##### 2.2 XML

XML 即**可扩展标记语言**,XML 和 HTML 虽然都是标记语言，但是它们两者之间没有任何的关系。

HTML 被设计用来描述网页上的内容，是**网页内容的载体**                 XML 被设计用来传输和存储数据，**是数据的载体**

XML的缺点：XML 格式臃肿，和数据无关的代码多，体积大，传输效率低在 Javascript 中解析 XML 比较麻烦

##### 2.3 JSON

###### 2.3.1

 JSON即“JavaScript 对象表示法”，本质是**字符串**，是一种轻量级的文本数据交换格式，专门用于存储和传输数据，比 XML 更小、更快、更易解析。JSON 已经成为了主流的数据交换格式。

###### 2.3.2JSON的两种结构:**对象和数组**两种结构，通过这两种结构的**相互嵌套**，可以表示各种复杂的数据结构。

**对象结构**：对象结构在 JSON 中表示为 { } 括起来的内容。数据结构为 { key: value, key: value, … } 的键值对结构。其中，key 必须是使用**英文的双引号**包裹的字符串，value 的数据类型可以是数字、字符串、布尔值、null、数组、对象6种类型。值如果是字符串也必须用双引号包裹，没有underfined,和function

**数组结构：**数组结构在 JSON 中表示为 [ ] 括起来的内容。数据结构为 [ "java", "javascript", 30, true … ] 。数组中数据的类型可以是数字、字符串、布尔值、null、数组、对象6种类型。

注意:属性名必须使用双引号包裹     字符串类型的值必须使用双引号包裹           JSON 中不允许使用单引号表示字符串

JSON 中不能写注释                   JSON 的最外层必须是对象或数组格式            不能使用 undefined 或函数作为 JSON 的值

###### 2.3.3JSON和JS对象的关系：

JSON 是 JS 对象的**字符串表示法**，它使用文本表示一个 JS 对象的信息，本质是一个字符串。

###### 2.3.4JSON和JS对象的互转

要实现从 JSON 字符串转换为 JS 对象，使用 JSON.**parse**(**'**JSON字符串**'**) 方法：   **反序列化**

要实现从 JS 对象转换为 JSON 字符串，使用 JSON.**stringify**(JS对象) 方法：   **序列化**

#### 3.封装自己的Ajax函数

##### 3.1 定义options参数选项

itheima() 函数是我们自定义的 Ajax 函数，它接收一个配置对象作为参数，配置对象中可以配置如下属性：

method   请求的类型            url   请求的 URL 地址                  data 请求携带的数据             success 请求成功之后的回调函数    

##### 3.2 处理data参数

需要把 data 对象，转化成查询字符串的格式，从而提交给服务器，因此提前定义 resolveData 函数体如下：

for (var k in data) {    arr.push(k + '=' + data[k])    }        return arr.join('&')

##### 3.4 定义itheima函数

在 itheima() 函数中，需要创建 xhr 对象，并监听 onreadystatechange 事件：

var xhr = new XMLHttpRequest()  // 拼接查询字符串  

var qs = resolveData(options.data)  // 监听请求状态改变的事件  

xhr.onreadystatechange = function() {    if (xhr.readyState === 4 && xhr.status === 200)

{   var result = JSON.parse(xhr.responseText)   ；options.success(result)    }  }

##### 3.5 判断请求的类型

不同的请求类型，对应 xhr 对象的不同操作，因此需要对请求类型进行 if … else … 的判断：

GET　　　xhr.open(options.method, options.url + '?' + qs)

POST　　　xhr.open(options.method, options.url)    xhr.setRequestHeader(．．．．．)

#### 4.XMLHttpRequest Level2的新特性

##### 4.1 认识XMLHttpRequest Level2

###### 4.1.1.旧版XMLHttpRequest的缺点　　

只支持文本数据的传输，无法用来读取和上传文件传送和接收数据时，没有进度信息，只能提示有没有完成

###### 4.1.2.XMLHttpRequest Level2的新功能　

可以设置 HTTP 请求的时限　　可以使用 FormData 对象管理表单数据　可以上传文件　可以获得数据传输的进度信息

##### 4.2 设置HTTP请求时限

新版本的 XMLHttpRequest 对象，增加了 **timeout** 属性，可以设置 HTTP 请求的时限：

示例： xhr.timeout = 3000（毫秒）与之配套的事件指定回调函数xhr.ontimeout = function(event){     alert('请求超时！') }

##### 4.3 FormData对象管理表单数据

Ajax 操作往往用来提交表单数据。为了方便表单处理，HTML5 新增了一个 FormData 对象，可以模拟表单操作：

var fd = new FormData()      　　　　　　　　　　　　　　 // 1. 新建 FormData 对象   

fd.append('uname', 'zs')      fd.append('upwd', '123456')　　　// 2. 为 FormData 添加表单项   

FormData对象也可以用来获取网页表单的值，关键代码如下： var fd = new FormData(form选择器)，其中form是通过DOM操作获取到的HTML元素

##### 4.4 上传文件

定义 UI 结构          <input type="file" id="file1" />    

验证是否选择了文件        关键代码 var files = document.querySelector('#file1')**.files** ,**数组**，然后判断 files的长度是否为0

向 FormData 中追加文件        fd.append(**'avatar'**, files[0])       

使用 xhr 发起上传文件的请求   上传方式必须使用**POST**,  xhr.open(....) xhr.send(fd)                         

监听 onreadystatechange 事件

##### 4.5 显示文件上传进度

新版本的 XMLHttpRequest 对象中，可以通过监听 xhr.**upload.onprogress** 事件，来获取到文件的上传进度。

 xhr.**upload.onprogress** = function(**e**) {             // 监听 xhr.upload 的 onprogress 事件

  if (**e.lengthComputable**) {       // e.lengthComputable 是一个布尔值，表示当前上传的资源是否具有可计算的长度  

  var percentComplete = Math.ceil((e.loaded / e.total) * 100)    } }   // e.loaded 已传输的字节        // e.total  需传输的总字节            

#### 5.jQuery高级用法

##### 5.1 jQuery实现文件上传

**contentType: false,**   // 不修改 Content-Type 属性，使用 FormData 默认的 Content-Type 值

**processData: false,**     // 不对 FormData 中的数据进行 url 编码，而是将 FormData 数据原样发送到服务器     

  **不要忘了把JQuery对象转化为DOM对象**

##### 5.2 jQuery实现loading效果

ajaxStart(callback) Ajax 请求开始时，执行 ajaxStart 函数。可以在 ajaxStart 的 callback 中显示 loading 效果，

$(document).ajaxStart(function() {     $('#loading').show() })

ajaxStop(callback)   Ajax 请求结束时，执行 ajaxStop 函数。可以在 ajaxStop 的 callback 中隐藏 loading 效果，

$(document).ajaxStop(function() {     $('#loading').hide() })

#### 6.axios

##### 6.1 什么是axios

Axios 是专注于**网络数据**请求的库。相比于原生的 XMLHttpRequest 对象，axios 简单易用。

相比于 jQuery，axios 更加轻量化，只专注于网络数据请求。

##### 6.2 axios发起GET请求

axios.**get**('url', {params:  { /*参数*/ }  }  ).then(callback)

console.log(**res.data**)与之前不同的是res.data才是服务器真正返回过来的数据，其他的都是Axios自加的

##### 6.3 axios发起POST请求

axios.**post**('url', { data:  { /*参数*/ }   }).then(callback)

res.data才是真正的数据

##### 6.4 直接使用axios发起请求

axios({     method: '请求类型',     url: '请求的URL地址',   

​                 data: { /* POST数据 */ }   ///  params: { /* GET参数 */ }         俩选一

​                 }) .**then**(callback)

### 四.Git

git常用命令

git config --list --global                       查看全局配置项

git config user.name                      git config user.email

git help config         git config -h          查看帮助

git init                                                       在现有目录中初始化仓库

文件有四种状态:未被跟踪，已跟踪(未修改，已修改，已暂存)

git status                    git status   -s              显示文件状态

git add +跟踪文件   暂存区A                        跟踪新文件

clear                                                                  清除

git commit -m+提交描述     未修改，在Git仓库中             提交更新

对已提交的文件进行修改查看状态变为已修改 M(红色)，还没有暂存

 git add           1.可以用它开始跟踪新文件把已跟踪的 2.且已修改的文件放到暂存区 ，状态未已暂存M(绿色) 3.把有冲突的文件标记为已解决状态

git commit -m            提交已暂存的文件

git checkout --文件名                                           撤销对文件的修改(危险度较高，无法还原用， Git 仓库中保存的文件，覆盖工作区中指定的文件)

git add .                    向暂存区中一次性添加多个文件

git reset HEAD 要移除的文件名称                                   取消暂存的文件

git commit -a -m "描述"                              跳过使用暂存区域

从 Git 仓库中移除文件的方式有两种：从 Git 仓库和工作区中同时移除对应的文件git rm -f 文件名

只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件

git rm --cached 文件名

16.忽略文件  一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可以创建一个名为 .gitignore 的配置文件，列出要忽略的文件的匹配模式。文件 .gitignore 的格式规范如下：

以 # 开头的是注释            以 / 结尾的是目录          以 / 开头防止递归以 ! 开头表示取反          可以使用 glob 模式进行文件和文件夹的匹配（glob 指简化了的正则表达式）

17.查看提交历史

git log     按时间先后列出所有的提交历史  git log -2        git  log  -2 --pretty=oneline展示两条一行显示   :"%h | %an | %ar | %s"

18.回退到指定的版本

git reset --hard <CommitID>

git reflog --pretty=oneline                              在旧版本中查看命令操作的历史

### 五.GitHub

开源许可协议：

GPL:具有传染性的一种开源协议，不允许修改后和衍生的代码做为闭源的商业软件发布和销售使用 GPL 的最著名的软件项目是：Linux

MIT：是目前限制最少的协议，唯一的条件：在修改后的代码或者发行包中，必须包含原作者的许可信息使用 MIT 的软件项目有：jquery、Node.js

git push将第一次之后的文件上传至github仓库

SSH

 master 主分支:用来保存和记录整个项目已完成的功能代码。

因此，不允许程序员直接在 master 分支上修改代码，因为这样做的风险太高，容易导致整个项目崩溃。

git branch                                                                                               查看分支列表   分支名字前面的 * 号表示当前所处的分支。

git branch 分支名称                                                                                     创建新分支

git checkout 分支名称                                                                                 切换分支

git checkout -b 分支名称                                                                            分支的快速创建和切换

git merge login 必须在master分支上运行                                                合并分支

git branch -d 分支名称                                                                                  删除分支

遇到冲突时的分支合并，如果在两个不同的分支中，对同一个文件进行了不同的修改，Git 就没法干净的合并它们。 此时，我们需要打开这些包含冲突的文件然后手动解决冲突。

git add .            git commit -m

 git push -u 远程仓库的名称(第一次，不是第一次省略-u)                     将本地分支推送到远程仓库

git remote show 远程仓库名称                                                                     查看远程仓库中所有的分支列表

git checkout -b 本地分支名称  远程仓库名称/远程分支名称                    跟踪分支

git pull                                                                                                                拉取远程分支的最新的代码

git push 远程仓库名称 --delete 远程分支名称                                             删除远程分支