              HTML和CSS是描述类语言， JavaScript是编程类语言( JS 产生最初的目的: 表单动态校验（密码强度检测）)

#### 一:初识 JavaScript(编程类语言)



1.1特点:一种**运行在客户端**的**脚本语言** ：**不需要编译**，运行过程中由 **js 解释器( js 引擎）逐行**来进行解释并执行

 

##### 1.2浏览器时怎么执行 JS 

浏览器分成两部分：**渲染引擎和 JS 引擎** 

**渲染引擎：**用来**解析HTML与CSS**，俗称**内核**，比如 chrome 浏览器的 blink ，老版本的 webkit

 **JS 引擎**：也称为 JS 解释器。 用来读取网页中的JavaScript代码，对其处理后运行，比如 chrome  浏览器的 V8



##### 1.3 JS 的组成

**ECMAScrip**(JavaScript语法)                 **DOM**(页面文档对象模型)             **BOM**(浏览器对象模型)   



##### 1.4引入方式

行内式      内嵌式(<script></script>)   引入式(<script src="my.js"></script>)  单引号

##### 1.5输入输出

alert(msg)       console.log(msg) 游览器控制台打印输出信息              prompt(info)游览器弹出输入框



#### 二:变量(容器，用来存放数据 本质:变量是程序在内存中申请的一块用来存放数据的空间)

使用:声明变量，赋值var,  不声明只赋值也能出结果，不建议           不赋值不报错，没结果，不建议

命名:变量命名**区分大小写**  

##### 2.1数据类型

JavaScript 是一种弱类型或者说动态语言。这意味着**不用提前声明变量的类型**，在程序运行过程中，**类型会被自动确定**。

JavaScript 拥有动态类型，同时也意味着**相同的变量可用作不同的类型**：



**分类:简单数据类型 （Number,String,Boolean,Undefined(未赋值),Null）  复杂数据类型 （object，Arrey,Date)**



**2.2数字型Number:**八进制前加0，十六进制前加0×          NaN非数值     **检测变量是否是数字型方法isNaN(变量值),返回Boolean值**



**2.3字符串型String: **  '12'也是字符串型   **单引号或双引号**              字符串值嵌套:用单引号嵌套双引号或双引号嵌套单引号    

转义符: 空格:  **\b** html中空格(&nbsp ;)   **\n**换行

**检测获取字符串长度方法 变量值.length**

**字符串拼接**        字符串 **+**任何类型        



**2.4布尔型Boolean**            

注意:当命名了一个变量是ture,执行console.log(变量+1)得到结果是2   当为false,就是1



**2.5未定义型undefined**          未赋值或者直接定义 **var variable= undefined ；**

**注意点:console.log('你好' +undefined);  // 你好undefined         console.log(11 + undefined);     // NaN**



**2.6空值Null**  直接定义:var space= null; 

**注意点:console.log('你好' +null);//你好space  console.log(1 + null);//1**



2.7检测变量数据类型方法**(typeof 变量)**  返回数据类型          

**注意点: typeof Null返回Object ；输入输出语法prompt取过来的值是字符型**

除此之外:控制台颜色，数字型蓝色 ，字符串型是黑色  ，布尔型是深渊蓝 ，null和underfined是灰色；



2.8字面量         数字字面量：8, 9, 10        字符串字面量：'黑马程序员', "大前端"         布尔字面量：true，false

**2.9数据类型转换**

转换为字符串类型  

![image-20220909100403581](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909100403581.png)

转换为数字型 ![image-20220909100425462](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909100425462.png)

转换为布尔型   

![image-20220909100540045](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909100540045.png)

**代表空、否定的值会被转换为 false  ，如 '  '、0、NaN、null、undefined**    其余值都会被转换为 true



#### 三：运算符

注意:不要直接用浮点数运算，要转化为二进制,会有精度问题     也不建议拿浮点数直接比较

**3.1递增（++）和递减（ -- ）**既可以放在变量前面，也可以放在变量后面。放在变量前面时，我们可以称为前置递增（递减）运算符，放在变量后面时，我们可以称为后置递增（递减）运算符。 

num++ **后置递增：先返回原值，后自加1**

案例:var age = 10;    console.log(age++  +10 );   console.log(age);   输出依次是20，11       var e=10; var f=e++  +  ++e;结果为22

**3.2比较符**        **==       注意点:console.log(18 == '18'); // true**  会将字符串型转换为数字型，有隐式转换效果

​                          ===  全等一模一样  要求:两侧的值,还有数据类型完全一致才可以               !==



**3.3逻辑符号**  

**短路运算**的原理：当有多个表达式（值）时,左边的表达式值可以确定结果时,就不再继续运算右边的表达式的值;

**逻辑与&&     语法： 表达式1 && 表达式2             如果第一个表达式的值为真，则返回表达式2 ;反之则返回表达式1**

// 如果有空的或者否定的为假,例如: ' ' ,null,undefined ,NaN ,0     其余是真的 

**逻辑或   语法： 表达式1 || 表达式2                   如果第一个表达式的值为真，则返回表达式1 ;反之则返回表达式2**

案例: console.log(0 || 456 || 456 + 123); // 456

// **逻辑中断很重要 它会影响我们程序运行结果**

​    var num = 0;    console.log(123 || num++);    console.log(num); // 0



**3.4运算符优先符法则**

![image-20220908101524361](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908101524361.png)

案例:console.log( 4 >= 6 || **'人' != '阿凡达'** && **!(12 * 2 == 144)** && **true**)      先算后三个与&&



#### 四:流程控制

流程控制主要有三种结构，分别是顺序结构、分支结构和循环结构，这三种结构代表三种代码执行的顺序。

**三元表达式:**    **条件表达式 ? 表达式1 : 表达式2;**



**4.1switch语句**  switch( 表达式 ){     case value1: 执行语句1;break;    case value2:   执行语句2  ;break;    default:    最后执行的语句}

注意:变量的值和 case里面的值相匹配的时候是全等=== ，必须是**值和数据类型一致才可以**

如果进入当前的case里面没有break，则不会退出switch，是继续执行下一个case里的语句，**并且不会再次判定下一个case**，直接执行下一个case里的执行代码



#### 五.循环控制

 for 循环           while 循环          do...while 循环                         (一组被重复执行的语句被称之为循环体)

**断点调试**是指自己在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。浏览器中按 F12--> sources -->找到需要调试的文件-->在程序的某一行设置断点Watch: 监视，通过watch可以监视变量的值的变化，非常的常用。F11: 程序单步执行，让程序一行一行的执行，这个时候，观察watch中变量的值的变化。箭头符号执行下一步

while(条件表达式){循环体}        do{循环体}while(条件表达式) ;do while至少执行一次循环体



continue 关键字用于立即跳出本次循环，继续下一次循环（本次循环体中 continue 之后的代码就会少执行一次）。

break 关键字用于立即跳出整个循环（循环结束）

。

#### 六.数组Arrey

数组是将一组数据存储在单个变量名下的优雅方式，其中的每个数据被称作元素，在数组中可以存放**任意类型的元素**。

**6.1创建数组**         

利用new 创建数组 : var 数组名 = new Array() ；  

利用数组字面量创建数组: var  数组名 = []；

**6.2遍历数组**        

可以通过索引来访问、设置、修改对应的数组元素，可以通过“**数组名[索引]**(下标从0)”的形式来获取数组中的元素。

**6.3数组长度**       使用“**数组名.length**”可以访问数组元素的数量（数组长度）。

**6.4数组新增**     

通过修改 length 长度新增数组长度 arr.length = 7;           

通过修改数组索引新增数组元素arr[4] = 'hotpink';      如果已经有原来的元素，则会替换原来的数组元素

注意:不要直接给数组名赋值，否则里面的数组元素都没有了



翻转数组:  i=原数组.length-1；i>=0;i--

**6.5冒泡排序**

 每一次排序都能把最大值/最小值放在最右边/次右边       外循环执行length-1次，里循环替换原数组.length-i-1



#### 七 .函数(封装了一段可被重复调用执行的代码块)。

**7.1.声明函数**   

方式一:**function 函数名(形参1，形参2) {    函数体代码  }**    (通常将函数名命名为动词，比如 getSum)   

方式二:函数表达式方式 (匿名函数）**var fn = function(){ 函数体代码}；** **此时fn是变量名**

**7.2使用函数:**   **函数名(实参1, 实参2, 实参3...);** 

**7.3 函数形参和实参个数不匹配问题**

![image-20220908132910099](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908132910099.png)

**7.4.return**  只能返回一个值(**可以是数组**)。如果用逗号隔开多个值，**以最后一个为准**。 **如果没有return 则返回 undefined** 



**7.5arguments**

当不确定有多少个参数传递的时候，可以用 arguments 来获取。**arguments 实际上它是当前函数的一个内置对象**。

**所有函数都内置了一个 arguments 对象，arguments 对象中存储了传递的所有实参。**

arguments展示形式是一个**伪数组**，因此可以进行**遍历**。伪数组具有以下特点：具有 **length 属性按索引方式储存数据**    不具有数组的 **push , pop** 等方法         



**7.6作用域:**代码范围就是这个名字的作用域。(目的是为了提高程序的可靠性更重要的是减少命名冲突)

全局作用域:作用于所有代码执行的环境(整个 script 标签内部)或者一个独立的 js 文件。

局部作用域（函数作用域）:作用于函数内的代码环境，就是局部作用域。 



**7.6**根据作用域的不同，变量可以分为两种：

**全局变量：**在代码的任何位置都可以使用，在全局作用域下 var 声明的变量是全局变量，特殊情况下，在**函数内不使用** **var 声明的变量**也是全局变量（不建议使用）

**局部变量:**只能在该函数内部使用在函数内部   **var 声明的变量是局部变量** ,函数的**形参**实际上就是局部变量

特点:全局变量只有浏览器关闭的时候才会销毁，比较占内存资源     (2) 局部变量 当我们程序执行完毕就会销毁， 比较节约内存资源





**7.8作用域链:****根据在内部函数可以访问外部函数变量的这种机制，用**链式查找决定哪些数据能被内部函数访问,来决定取那个值**，就称作作用域链;**(就近原则)**

注意:JS没有块作用域



**7.9.预解析**

JavaScript代码是由浏览器中的 JavaScript解析器来执行的。JavaScript 解析器在运行 JavaScript 代码的时候分两步：预解析和代码执行。



预解析：在当前作用域下, JS 代码执行之前，浏览器会默认把**带有 var 和 function 声明的变量在内存中进行提前声明或者定义**。

代码执行： 从上到下执行JS语句。

**变量提升：** **变量的声明会被提升到当前作用域的最上面，但是变量的赋值不会提升**。

案例:console.log(num);  var num = 10; // 结果是多少？    相当于  var num;console.log(num);num=10;        输出underfined

**函数提升： 函数的声明会被提升到当前作用域的最上面，但是不会调用函数。**

案例:var num = 10;  fun();    function fun() { console.log(num);  var num = 20;}      根据作用域链的就近法则,console里输出的值是函数里的num,但是在变量提升只声明不赋值，所以输出underfined       

案例1:

f1();console.log(c);console.log(b);console.log(a);function f1() {  var a = b = c = 9;  console.log(a);  console.log(b);  console.log(c);}

var a = b = c = 9;相当于:相当于 var  a  = 9; b = 9; c = 9;**b,c是全局变量**





#### **八:对象**一组无序的相关**属性和方法**的集合，**复杂数据类型Object**

**8.1创建对象:**    三种方法:利用字面量创建对象       利用 new Object 创建对象        利用构造函数创建对象

**8.2：利用字面量创建对象 ** **var 对象名={}**

 var obj = { uname: '张三疯',      age: 18,    sayHi: function() {  console.log('hi~');  }    }

注意:(1) 里面的属性或者方法我们采取键值对的形式  属性名(键) ：属性值(值) 

(2) 多个属性或者方法中间用**逗号**隔开的

(3) 方法冒号后面跟的是一个匿名函数

**8.2.使用对象:**  调用**对象的属性**        **对象名.属性名  obj.uname**              **对象名['属性名']**   **obj['age']**

​                           调用**对象的方法**         **对象名.方法名()**    obj.sayHi();



 **8.3利用 new Object 创建对象**    **var 对象名 = new Object();**

 var obj = new Object();   obj.uname = '张三疯';  obj.sayHi = function() {  console.log('hi~');  }



**8.4利用构造函数创建对象**    

前两种创建对象的方式一次只能创建一个对象,当多个对象的属性和方法基本相同时,我们只能复制,因此可以利用函数的方法,重复利用这些代码,我们就把这个函数成为构造函数.又因为这个函数不一样，里面封装的不是普通代码，而是**对象** ;

 **构造函数:就是把我们对象里面一些相同的属性和方法抽象出来封装到函数里面**

**利用构造函数创建对象**:function 构造函数名() {  this.属性 = 值; this.方法 = function() {} }



创建四大天王的对象  相同的属性： 名字 年龄 性别  相同的方法： 唱歌

**创建构造函数**:function **Star ** (uname, age, sex) {             **构造函数名字首字母要大写**

​      **this.**name = uname;

​      **this.**age = age;

​      **this.**sex = sex;

​      **this.**sing = **function**(sang) {

​        console.log(sang);

​      }

​    }

**构造函数不需要return 就可以返回结果**  

**调用构造函数:** var ldh = **new** Star('刘德华', 18, '男'); ldh.sing('冰雨');              **调用构造函数 必须使用 new**

区别:构造函数(明星泛指的某一大类),对象特指是一个具体的事物,我们利用**构造函数创建对象的过程我们也称为对象的实例化**



**8.5.构造函数关键字New执行过程**

1.new 构造函数可以在内存中创建了一个空的对象                             2.this 就会指向刚才创建的空对象

3.执行构造函数里面的代码,给这个空对象添加属性和方法                 4.返回这个对象

**8.6遍历对象属性**

for...in 语句用于对数组或者对象的属性进行循环操作。

**for** ( **var ** 变量 **in** 对象名字) {   执行代码  }

**for (var k in obj)** { **console.log(k);   // 输出这里的 k 是属性名**      **console.log(obj[k]); // 这里的 obj[k] 是属性值}**





#### **九:内置对象**

**9.1简介:**JavaScript 中的对象分为3种：自定义对象 、**内置对象**、 浏览器对象(前面两种对象是JS基础内容，属于 ECMAScript；  第三个浏览器对象属于JS 独有的)

**内置对象**就是**指 JS 语言自带的一些对象**，这些对象供开发者使用，并提供了一些**常用的或是最基本而必要的功能（属性和方法）**内置对象最大的优点就是帮助我们**快速开发**. JavaScript 提供了多个内置对象：Math、 Date 、Array、String,arguments 等



9.2.文档**MDN**  https://developer.mozilla.org/zh-CN/



**9.3.Math()对象:**    

Math.PI// 圆周率        Math.floor() // 向下取整       Math.ceil()  // 向上取整            Math.round() // 四舍五入就近取整(0.5小数往数值大取)          Math.abs()// 绝对值                Math.max()/Math.min()// 求最大和最小值

注意：Math.max()  如果参数则结果为 - [`Infinity`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Infinity);如果有任一参数不能被转换为数值，则结果为 [`NaN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/NaN)。

Math.abs()有**隐式转换效果**        



**9.4随机数方法  Math.random();**       生成随机小数,返回随机小数**[0,1)**

得到一个包括两数之间随机整数公式 

function getRandom(min, max) {  return **Math.floor(Math.random() * (max - min + 1)) + min;** }



9.5**日期对象Date  **

Date 对象和 Math 对象不一样，他是一个**构造函数**，需要**实例化**后才能使用

**var date = new Date();**     如果没有参数 返回当前系统的当前时间    

​                                              参数常用的写法             数字型  **2019, 10, 01**             字符串型 '**2019-10-1 8:8:8**'

**日期格式化: **      **getMonth()返回的月份小1个月(因为范围是0~11)  记得月份+1**  同样的,也要注意getDay()

![image-20220908220434588](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908220434588.png)

  Date 对象是基于1970年1月1日（世界标准时间）起的毫秒数



  **获取日期的总的毫秒形式**    获得Date总的毫秒数(时间戳) ，不是当前时间的毫秒数，**而是距离1970年1月1号过了多少毫秒数**

1. 通过 valueOf()或者getTime()

​    var date = new Date();                                                                     //Date是构造函数名

​    console.log(date.valueOf()); 或者console.log(date.getTime());       // 就是 我们现在时间 距离1970.1.1 总的毫秒数



2. 简单的写法 (**最常用的写法**)

​    **var date1 = +new Date(time);** // +new Date()   **如果参数为空返回的就是总的毫秒数**

​    console.log(date1);

3. H5 新增的 获得总的毫秒数    

​    console.log(Date.now());



倒计时案例: d = parseInt(总秒数/ 60/60 /24);    //  计算天数            h = parseInt(总秒数/ 60/60 %24) // 计算小时 

​                     m = parseInt(总秒数 /60 %60 );     //  计算分数                 s = parseInt(总秒数%60);//   计算当前秒数 

**9.6.数组对象Array()**              

创建数组对象的两种方式        **字面量方式           new Array()**

var arr1 = new Array(2);  // 这个2 表示 数组的长度为 2  里面有2个空的数组元素

var arr1 = new Array(2, 3); // 等价于 [2,3]  这样写表示 里面有2个数组元素 是 2和3



检测是否是数组两种方法:

**instanceof 运算符，**可以判断一个对象是否属于某种类型    **console.log( 对象 instanceof 数据类型);**返回布尔型

**Array.isArray(参数) **用于判断一个对象是否为数组，isArray() 是 HTML5 中提供的方法,ie9以上才支持



**添加,删除数组元素:**

![image-20220908224040555](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908224040555.png)

**数组排序**

![image-20220908224735914](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908224735914.png)

sort排序有时会有问题

arr1.sort(function(a, b) {

​      //  return a - b; 升序的顺序排列

​      return b - a; // 降序的顺序排列

​    });

**数组索引:**

![image-20220908225302277](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908225302277.png)

console.log(数组对象名.indexOf(数据类型));



**数组转换为字符串:**![image-20220908231605795](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908231605795.png)

  console.log(arr.toString()); // 1,2,3                                 console.log(arr1.join('-')); // green-blue-pink



![image-20220908231840469](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908231840469.png)



 var str = 'andy';    console.log(str.length);  简单数据类型为什么会有length 属性呢

基本包装类型:**把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。**

JavaScript 还提供了三个特殊的引用类型：String、Number和 Boolean

// (1) 把简单数据类型包装为复杂数据类型 

​    var temp = new String('andy');

​    // (2) 把临时变量的值 给 str

​    str = temp;

​    // (3) 销毁这个临时变量

​    temp = null;



**9.7字符串对象**

**字符串的不可变**:指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中**新开辟了一个内存空间。**

由于字符串的不可变，在大量拼接字符串的时候会有效率问题

**根据字符返回位置**

![image-20220908233037030](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908233037030.png)

**根据位置返回字符**

![image-20220908234605965](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220908234605965.png)



案例： 判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数。

​            核心算法：利用 charAt(） 遍历这个字符串

​           把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1

​           遍历对象，得到最大值和该字符 



**字符串操作方法**

![image-20220909000206790](C:\Users\Wu FeiHang\AppData\Roaming\Typora\typora-user-images\image-20220909000206790.png)



**字符串替换** replace()方法        replace(被替换的字符串， 要替换为的字符串)；只替换第一个能找到的字符

 // 有一个字符串 'abcoefoxyozzopp'  要求把里面所有的 o 替换为 *

​    var str1 = 'abcoefoxyozzopp';

​    while (str1.indexOf('o') !== -1) {

​      str1 = str1.replace('o', '*');

​    }

​    console.log(str1);



**字符转换为数组**  split( 切割符)       split()方法用于切分字符串，它可以将字符串切分为数组。

var str = 'a,b,c,d';console.log(str.split(','));   // 返回的是一个数组 [a, b, c, d]

与之前的数组转为字符串，toString()和join(’分隔符‘)对应



#### 十:简单数值类型和复杂数据类型



**10.1简单数值类型**,值类型   **存储变量存储的值是本身** string number float null  bootlean underfined

**10.2复杂数值类型**,引用类型   **存储时变量中存储的仅仅是地址(引用)**      通过new关键字创建的对象  date,arrey,object



**10.3堆和栈**

栈:由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈； **简单数据类型存放到栈里面**

堆:存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。 **复杂数据类型的值存放到堆里面,地址在栈**

**10.4简单类型传参**

函数的形参也可以看做是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。

**10.5复杂类型传参**

函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。
