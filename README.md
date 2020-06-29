# 前端

## HTML

### 语义化

- 用正确的标签做正确的事情
- HTML语义化就是让页面的内容结构化，便于对浏览器、搜索引擎解析
- 在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的
- 搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO

### 新特性

- 绘画 canvas
- 用于媒介回放的 video 和 audio 元素
- 存储localStorage ，sessionStorage 
- 语意化更好的内容元素，比如article、footer、header、nav、section
- 表单控件，calendar、date、time、email、url、search
- 新的技术webworker、 websocket、 Geolocation

### 行内元素

- a b span img input select strong

### 块级元素有

- div ul ol li dl dt dd h1 h2 h3 h4… p

### 空元素

- <br> <hr> <img> <input> <link> <meta>

### viewport

<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
    // width    设置viewport宽度，为一个正整数，或字符串‘device-width’
    // device-width  设备宽度
    // height   设置viewport高度，一般设置了宽度，会自动解析出高度，可以不用设置
    // initial-scale    默认缩放比例（初始缩放比例），为一个数字，可以带小数
    // minimum-scale    允许用户最小缩放比例，为一个数字，可以带小数
    // maximum-scale    允许用户最大缩放比例，为一个数字，可以带小数
    // user-scalable    是否允许手动缩放

### src与href的区别

- src用于替换当前元素
- href用于在当前文档和引用资源之间确立联系

## CSS

### 权重

- important：无限高
- 行内样式：权重值为1000
- id选择器：权重值为100
- 类、伪类、属性选择器：权重值为10
- 元素选择器：权重值为1

### 盒模型

- 标准盒模型：标签得实际宽度 = 设置的宽度 + border宽度 + padding的宽度
- 怪异盒模型：标签得实际宽度 = 设置的宽度 

### BFC

- 块级格式上下文
- 触发BFC

  float的值不为none。
  overflow的值不为visible。
  display的值为table-cell、table-caption和inline-block之一。
  position的值不为static或releative中的任何一个。

### 清除浮动

.clear:after, .clear:before {
  content: ' ';
  display: table;
}
.clear:after {
  clear: both;
}

### em、rem的区别

- em：如果父级有设置字体大小，1em就是父级的大小，没有1em等于自身默认的字体大小
- rem：相对于html标签的字体大小

### 定位的方式

- relative：相较于自身定位，设置的位置相对于自己进行位移。不脱离文档流。
- absolute：相较于最近有定位的父节点定位，设置的位置相较于父节点。会脱离文档流，导致父节点高度塌陷。
- fixed：相较于当前窗口进行定位，设置的位置相较于窗口。脱离文档流。

### 垂直水平居中

- 父级设置text-align: center和line-height等同高度。
- 子节点绝对定位，设置position: absolute;top: 50%;left: 50%;transform: translate(-50%, -50%);
- 父级设置display: flex;justify-content:center;align-items:center;

### 重绘和回流

- 重绘是节点的外观发生改变而不改变布局时，如改变了color这个行为
- 流是指改变布局或几何属性发生改变时引起的行为，如添加移除Dom，改变尺寸。它们频繁的触发会影响页面性能。
- 回流一定触发重绘，而重绘不一定引起回流。回流的成本比重绘高很多，而且子节点的回流，可能引起父节点一系列的回流
- 如何减少重绘和回流

  使用transform替代位移，使用translate3d开启GPU加速
  尽量使用visibility替代display:none
  不要使用tanle布局
  不要在循环里读取节点的属性值
  动画速度越快，回流次数越少

## JS

### 数据类型

- 基本类型

  number
  string
  boolena
  null
  undefined
  symbol

- 复杂类型

  object

- null 和 undefined 的区别

  undefined 代表的含义是未定义， null 代表的含义是空对象

### 闭包

闭包就是能够读取其他函数内部变量的函数.
用途:1访问函数内部的变量;2防止函数内部执行完后被销毁

function a(){ 
	var n = 0;
 	function add(){ 
		n++; console.log(n);
	 } 
	return add;
 } 
var a1 = a(); //注意，函数名只是一个标识（指向函数的指针），而（）才是执行函数；
 a1(); //1 
a1(); //2 第二次调用n变量还在内存中

### 作用域

- 作用域

  作用域是定义变量的区域，它有一套访问变量的规则，这套规则来管理浏览器引擎如何在当前作用域以及嵌套的作用域中根据变量（标识符）进行变量查找。

- 作用域链

  作用域链的作用是保证对执行环境有权访问的所有变量和函数的有序访问，通过作用域链，我们可以访问到外层环境的变量和 函数。

### 构造函数

- new关键字做了什么

  创建一个新的对象
  将新对象指向构造函数,绑定 this
  执行构造函数中的代码
  返回新的对象

- 构造函数-原型-实例三者关系

	- 原型链

	  每个对象都有prototype属性,通过这一属性可以找到它的原型对象,原型对象也有prototype属性,以此类推,形成原型链.查找属性时,先去对象本身查找,找不到就去原型链找寻.
	  一直找到Object.prototype ；如果中间找到会停止查找返回该方法。如果一直没找到会返回未定义；

- 类数组转真数组

	- Array.prototype.slice.call()
	- Array.from(arguments)
	- [...arguments]

### 继承

- 1、原型链继承

  父类的实例=子类的原型
  function People(name){
    //属性
    this.name  = name || Annie
    //实例方法
    this.sleep=function(){
      console.log(this.name + '正在睡觉')
    }
  }
  function Woman(){ 
  }
  Woman.prototype= new People();
  Woman.prototype.name = 'haixia';
  let womanObj = new Woman();
  优点：
  简单易于实现，父类的新增的实例与属性子类都能访问
  缺点：
  可以在子类中增加实例属性，如果要新增加原型属性和方法需要在new 父类构造函数的后面
  无法实现多继承
  创建子类实例时，不能向父类构造函数中传参数

- 2、借用构造函数继承

  复制父类的实例属性给子类
  function Woman(name){
   //继承了People
    People.call(this); //People.call(this，'wangxiaoxia'); 
    this.name = name || 'renbo'
  }
  let womanObj = new Woman();
  优点：
  解决了子类构造函数向父类构造函数中传递参数
  可以实现多继承（call或者apply多个父类）
  缺点：
  方法都在构造函数中定义，无法复用
  不能继承原型属性/方法，只能继承父类的实例属性和方法

- 3、实例继承

  function Wonman(name){
    let instance = new People();
    instance.name = name || 'wangxiaoxia';
    return instance;
  }
  let wonmanObj = new Wonman();
  优点：
  不限制调用方式
  简单，易实现
  缺点：不能多次继承

- 4、组合式继承

  调用父类构造函数，继承父类的属性，通过将父类实例作为子类原型，实现函数复用
  unction People(name,age){
    this.name = name || 'wangxiao'
    this.age = age || 27
  }
  People.prototype.eat = function(){
    return this.name + this.age + 'eat sleep'
  }
  
  function Woman(name,age){
    People.call(this,name,age)
  }
  Woman.prototype = new People();
  Woman.prototype.constructor = Woman;
  let wonmanObj = new Woman(ren,27);
  wonmanObj.eat(); 
  缺点：
  由于调用了两次父类，所以产生了两份实例
  优点：
  函数可以复用
  不存在引用属性问题
  可以继承属性和方法，并且可以继承原型的属性和方法

- 5、es6继承

  //class 相当于es5中构造函数
  //class中定义方法时，前后不能加function，全部定义在class的protopyte属性中
  //class中定义的所有方法是不可枚举的
  //class中只能定义方法，不能定义对象，变量等
  //class和方法内默认都是严格模式
  //es5中constructor为隐式属性
  class People{
    constructor(name='wang',age='27'){
      this.name = name;
      this.age = age;
    }
    eat(){
      console.log(`${this.name} ${this.age} eat food`)
    }
  }
  //继承父类
  class Woman extends People{ 
     constructor(name = 'ren',age = '27'){ 
       //继承父类属性
       super(name, age); 
     } 
      eat(){ 
       //继承父类方法
        super.eat() 
      } 
  } 
  let wonmanObj=new Woman('xiaoxiami'); 
  wonmanObj.eat();

- 总结

  第一种是以原型链的方式来实现继承，但是这种实现方式存在的缺点是，在包含有引用类型的数据时，会被所有的实例对象所共享，容易造成修改的混乱。还有就是在创建子类型的时候不能向超类型传递参数。
  第二种方式是使用借用构造函数的方式，这种方式是通过在子类型的函数中调用超类型的构造函数来实现的，这一种方法解决了不能向超类型传递参数的缺点，但是它存在的一个问题就是无法实现函数方法的复用，并且超类型原型定义的方法子类型也没有办法访问到。 
  第三种方式是组合继承，组合继承是将原型链和借用构造函数组合起来使用的一种方式。通过借用构造函数的方式来实现类型的属性的继承，通过将子类型的原型设置为超类型的实例来实现方法的继承。这种方式解决了上面的两种模式单独使用时的问题，但是由于我们是以超类型的实例来作为子类型的原型，所以调用了两次超类的构造函数，造成了子类型的原型中多了很多不必要的属性。 
  第四种方式是原型式继承，原型式继承的主要思路就是基于已有的对象来创建新的对象，实现的原理是，向函数中传入一个对象，然后返回一个以这个对象为原型的对象。这种继承的思路主要不是为了实现创造一种新的类型，只是对某个对象实现一种简单继承，ES5 中定义的 Object.create() 方法就是原型式继承的实现。缺点与原型链方式相同。 
  第五种方式是寄生式继承，寄生式继承的思路是创建一个用于封装继承过程的函数，通过传入一个对象，然后复制一个对象的副本，然后对象进行扩展，最后返回这个对象。这个扩展的过程就可以理解是一种继承。这种继承的优点就是对一个简单对象实现继承，如果这个对象不是我们的自定义类型时。缺点是没有办法实现函数的复用。 
  第六种方式是寄生式组合继承，组合继承的缺点就是使用超类型的实例做为子类型的原型，导致添加了不必要的原型属性。寄生式组合继承的方式是使用超类型的原型的副本来作为子类型的原型，这样就避免了创建不必要的属性。

### this

谁调用的this，this就指向谁
在浏览器里，在全局范围内this 指向window对象
在函数中，this永远指向最后调用他的那个对象；
构造函数中，this指向new出来的那个新的对象；
call、apply、bind中的this被强绑定在指定的那个对象上；
箭头函数中this比较特殊,箭头函数this为父作用域的this，不是调用时的this.要知道前四种方式,都是调用时确定,也就是动态的,而箭头函数的this指向是静态的,声明的时候就确定了下来；

### dom

- 查看视口的尺寸

	- document.body.clientWidth/clientHeight

- 查看元素的位置

	- dom.offsetLeft, dom.offsetTop

	  对于无定位父级的元素，返回相对文档的坐标。对于有定位父级的元素，返回相对于最近的有定位的父级的坐标。(无论是 left 还是margin-left等都是距离。 )

- 创建新节点

	- createDocumentFragment()    //创建一个DOM片段
	- createElement()   //创建一个具体的元素
	-  createTextNode()   //创建一个文本节点
	- appendChild(node) 、//添加

- 移除

	- removeChild(node)

- 替换

	- replaceChild(new,old)

- 插入

	- insertBefore(new,old)

- 查找

	- getElementById();
	- getElementsByName();
	- getElementsByTagName();
	- getElementsByClassName()
	- querySelector()
	- querySelectorAll()

- 属性操作

	- getAttribute(key)
	- setAttribute(key, value)
	- hasAttribute(key)
	- removeAttribute(key)

- 浏览器距离

	- document.documentElement.clientHeight：当前窗口内容区 + 内边距的高度
	- window.innerHeight: 当前窗口内容区 + 内边距 + 边框 + 滚动条高度
	- window.outerHeight：整个浏览器的高度(包括工具栏)
	- scrollHeight: 当前内部可以滚动区域的高度，如果不能滚动则为自己内容区 + 内边距的高度
	- scrollTop: 当前元素滚动离顶部的距离

- 元素距离

	- clientHeight: 当前元素内容区 + 内边距的高度
	- clientTop: 当前元素上边框的宽度
	- offsetHeight: 当前元素内容区 + 内边距 + 边框 + 滚动条的高度
	- offsetTop: 当前元素的边框距离父元素上外边距的距离

### bom

- cookie

	- cookie是服务器发送到用户浏览器并保存在本地的一小块数据，它会在浏览器发起请求时被携带并发送到服务器，它通常是告知服务端两个请求是否来自同一浏览器，保持用户的登录状态。
	- cookie保存的数据不能超过4k
	- 会随请求发送到服务端，可设置过期时间

- session

	- session代表着服务器在和客户端一次会话的过程，存储着用户会话所需的属性及配置信息，当用户在不同页面之间跳转时，使整个用户会话一直存在。

- localStorage

	- localStorage:存储大小为5M
	- 不参与请求，除非被清理，否则一直存在

- sessionStorage

	- 存储大小为5M
	- 不参与请求，页面关闭清除

- indexDB

	- 存储大小没限制
	- 不参与请求，除非被清理，否则一直存在，运行在浏览器上的非关系型数据库

### 事件

- 绑定

	- ele.onxxx = function (event) {}

	  兼容性很好，但是一个元素只能绑定一个处理程序，属性赋值会被覆盖 基本等同于写在HTML行间上

	- ele.addEventListener(type事件类型, fn处理函数, false);

	  IE9以下不兼容，可以为一个事件绑定多个处理程序

	- ele.attachEvent(‘on’ + type, fn); 

	  IE独有，一个事件同样可以绑定多个处理程序

- 解除

	- ele.onclick = false/‘’/null;
	- ele.removeEventListener(type, fn, false);
	- ele.detachEvent(‘on’ + type, fn);

- 事件传播

	- 捕获阶段=》目标阶段=》冒泡阶段
	- 事件传播的阻止

		- stopPropagation()

	- 阻止默认行为

		- preventDefault()

- 事件委托

  利用事件流的冒泡特性，将子节点的事件绑定在父节点上，然后在回调里面使用事件对象进行区分，优点是节省内存且不需要给子节点销毁事件。

- 鼠标事件

	- onmouseover、onmouseout

		- 支持事件冒泡

	- onmouseenter、onmouseleave

- 事件对象

  这个对象里面存放着触发事件的状态，如触发事件的当前元素，键盘事件是哪个按键触发的，滚动事件的位置等等

### 内置对象

- Array

	- 方法

		- unshift()开头增加

		  unshift( )  数组开头增加
		  功能：给数组开头增加一个或多个
		  参数：一个或多个
		  返回值：数组的长度
		  原数组发生改变

		- shift()开头删除一项

		  shift( )    数组开头删除一项
		  功能：给数组开头删除一个
		  参数：无
		  返回值：被删除的内容
		  原数组发生改变

		- push()末尾增加

		  push( )   数组末尾增加
		  功能：给数组末尾增加一项或多项
		  参数：一个或多个
		  返回值：数组的长度
		  原数组发生改变

		- pop()末尾删除一项

		  pop( )    数组末尾删除一项
		  功能：给数组末未删除一项
		  参数：无
		  返回值：被删除的内容
		  原数组发生改变

		- concat()拼接

		  concat( )  数组的拼接
		  ary1.concat( ary2,ary3....)
		  使用concat可以实现数组的克隆，concat（）中不传参数

		- splice(index, howmany, item1, ...itemx)可以根据参数实现数组的删除，增加，替换

		  splice（index, howmany, item1, ...itemx）
		  splice 可以根据参数实现数组的删除，增加，替换
		  前两个参数 index 和 howmany 是必需的参数，后面的参数可选参数
		  
		  splice（index, 0 ，item1， item2...)  增加
		  从索引 index 开始增加，增加的内容插入到索引 index 前面
		   
		  splice(index, n)  删除
		  从索引 index 开始删除n个，如果只有一个参数splice（index），就是从索引 index 开始后面的内容全部删除
		   
		  splice（index， n，item1，item2...） 替换
		  从索引 index开始替换 n 个，替换的内容为item1, item2....

		- slice(n,m)截取

		  slice（n，m）   截取
		  从索引 n 截取到索引 m 但不包括 m ，原数组不发生改变
		  slice（0）或splice（）可以实现数组的克隆

		- reverse() 数组翻转

		  返回值是翻转后的新数组，原数组发生改变

		- sort()数组排序

		  sort（）  数组排序
		  使用方法：sort（function （a，b）{return a-b}）  从小到大排
		          sort（function （a，b）{return b-a}）  从大到小排

		- toString()数组转字符串

		  toString( ) 数组转字符串
		  把数组转成以逗号分隔的字符串

		- join(拼接形式) 拼接

		  把数组拼接成以其他形式分割的字符串，配合eval（）可以实现数学运算    eval（join（‘+’））

		- indexOf(查找内容)查找

		  查找数组中是否有某项，有的话返回该项的所引，没有话返回-1

		- forEach()

		  forEach接收两个参数，一个callback，thisArg
		  callback接收三个参数：1）item 2）index 3）input
		  thisArg用来改变callback中的this指向；
		  forEach 没有返回值，但是map有返回值

		- map()
		- every()	检测数值元素的每个元素是否都符合条件。
		- filter()	检测数值元素，并返回符合条件所有元素的数组。
		- find()	返回符合传入测试（函数）条件的数组元素。
		- findIndex()	返回符合传入测试（函数）条件的数组元素索引。
		- indexOf()	搜索数组中的元素，并返回它所在的位置。
		- some()	检测数组元素中是否有元素符合指定条件。
		- isArray()	判断对象是否为数组。

	- 题目

		- 类数组转为数组

			- [].slice.call(arguments)
			- Array.from(arguments)
			- [...arguments]

		- 判断一个变量是否是数组

			- arr instanceof Array
			- Array.prototype.isPrototypeOf(arr)
			- Array.isArray(arr)
			- Object.prototype.toString.call(arr) === '[object Array]'
			- arr.constructor === Array

		- 多维数组扁平化

			- arr.flat(Infinity)

		- 数组去重

			-  [...new Set(arr)]

- String

	- 方法

		- charAT(index)通过索引找字符
		- charCodeAt(index)通过索引找到字符的 Unicode 编码。这个返回值是 0 - 65535 之间的整数。
		- indexOf() 从前往后找，找到返回内容的索引，找不到返回-1
		- lastIndexOf()从后往前找，找到返回内容的索引，找不到返回-1
		- slice()提取字符串的片断，并在新的字符串中返回被提取的部分。
		- split()	把字符串分割为字符串数组。
		- startsWith()	查看字符串是否以指定的子字符串开头。
		- substr()	从起始索引号提取字符串中指定数目的字符。

		  string.substr(start,length)

		- substring()	提取字符串中两个指定的索引号之间的字符。

		  string.substring(from, to)

		- toLowerCase()	把字符串转换为小写。
		- toUpperCase()	把字符串转换为大写。
		- trim()	去除字符串两边的空白

	- 题目

		- 字符串的test、match、search它们之间的区别

			- `test`是检测字符串是否匹配某个正则，返回布尔值；
			- `match`是返回检测字符匹配正则的数组结果集合，没有返回`null`；
			- `search`是返回正则匹配到的下标，没有返回`-1`。

		- 字符串的slice、substring、substr它们之间的区别

			- `slice`是返回字符串开始至结束下标减去开始下标个数的新字符串，下标是负数为倒数；

			  'abcdefg'.slice(2,3);  // c  // 3 - 2
			  'abcdefg'.slice(3,2);  // ''  // 2 - 3
			  'abcdefg'.slice(-2,-1);  // f  // -1 - -2

			- `substring`和`slice`正常截取字符串时相同，负数为0，且下标值小的为开始下标；

			  'abcdefg'.substring(2,3); //c // 3 - 2 'abcdefg'.substring(3,2); // c // 3 - 2 'abcdefg'.substring(3,-3); // abc // 3 - 0

			- `substr`返回开始下标开始加第二个参数(不能为负数)个数的新字符串。

			  'abcdefg'.substr(2, 3);  // cde
			  'abcdefg'.substr(3, 2);  // de
			  'abcdefg'.substr(-3, 2); // ef

- Number 

	- toFixed(x)	把数字转换为字符串，结果的小数点后有指定位数的数字。
	- toString()	把数字转换为字符串，使用指定的基数。

- Math

	- abs(x)	返回 x 的绝对值。
	- ceil(x)	对数进行上舍入。
	- floor(x)	对 x 进行下舍入。
	- max(x,y,z,...,n)	返回 x,y,z,...,n 中的最高值。
	- min(x,y,z,...,n)	返回 x,y,z,...,n中的最低值。
	- random()	返回 0 ~ 1 之间的随机数。

	  1 到 10 之间的一个随机数
	  Math.floor((Math.random()*10)+1);

- Date

	- getDate()	从 Date 对象返回一个月中的某一天 (1 ~ 31)。
	- getDay()	从 Date 对象返回一周中的某一天 (0 ~ 6)。
	- getFullYear()	从 Date 对象以四位数字返回年份。
	- getHours()	返回 Date 对象的小时 (0 ~ 23)。
	- getMilliseconds()	返回 Date 对象的毫秒(0 ~ 999)。
	- getMinutes()	返回 Date 对象的分钟 (0 ~ 59)。
	- getMonth()	从 Date 对象返回月份 (0 ~ 11)。
	- getSeconds()	返回 Date 对象的秒数 (0 ~ 59)。
	- getTime()	返回 1970 年 1 月 1 日至今的毫秒数。

- 正则
- Global

	- decodeURI()	解码某个编码的 URI。
	- decodeURIComponent()	解码一个编码的 URI 组件。
	- encodeURI()	把字符串编码为 URI。
	- encodeURIComponent()	把字符串编码为 URI 组件。
	- parseFloat()	解析一个字符串并返回一个浮点数。
	- parseInt()	解析一个字符串并返回一个整数。

### es6

- 说一些常用的 es6

  块作用域
  类
  箭头函数
  模板字符串
  加强的对象字面
  对象解构
  Promise
  模块
  Symbol
  代理（proxy）Set
  函数默认参数
  rest 和展开

- Promise 

	- Promise主要解决的问题就是异步回调嵌套过深造成代码难以维护和理解。
	- Promise构造函数内的代码是同步执行的，而之后then或catch方法是异步执行的，构造函数接受两个函数参数resolve和reject，它们执行时接受的参数分别会传递给then和catch表示成功的回调以及失败回调接受到的值。
	- Promise一共有三种状态pending等待状态、resolved已完成状态、rejected已拒绝状态，状态的改变只能由等待转为已完成或等待转为已拒绝状态，而且状态的改变只会发生一次。
	- 必须要实现then方法且方法里必须要返回一个Promise对象，如果是返回其他的类型会尝试包装成Promise对象；
then可以被链式的调用。
	- Promise 的几个特性

	  Promise 捕获错误与 try/catch 相同
	  Promise 拥有状态变化，并且状态变化不可逆
	  Promise 属于微任务
	  Promise 中的.then 回调是异步的
	  Promsie 中.then 每次返回的都是一个新的 Promise
	  Promise 会存储返回值

	- Promise 的简单实现

	  class MyPromise {
	    constructor(fn) {
	      this.resolvedCallbacks = [];
	      this.rejectedCallbacks = [];
	      this.state = "PADDING";
	      this.value = "";
	      fn(this.resolve.bind(this), this.reject.bind(this));
	    }
	    resolve(value) {
	      if (this.state === "PADDING") {
	        this.state = "RESOLVED";
	        this.value = value;
	        this.resolvedCallbacks.forEach(cb => cb());
	      }
	    }
	  
	    reject(value) {
	      if (this.state === "PADDING") {
	        this.state = "REJECTED";
	        this.value = value;
	        this.rejectedCallbacks.forEach(cb => cb());
	      }
	    }
	  
	    then(resolve = function() {}, reject = function() {}) {
	      if (this.state === "PADDING") {
	        this.resolvedCallbacks.push(resolve);
	        this.rejectedCallbacks.push(reject);
	      }
	      if (this.state === "RESOLVED") {
	        resolve(this.value);
	      }
	      if (this.state === "REJECTED") {
	        reject(this.value);
	      }
	    }
	  }

- var,let和const的区别是什么

  var声明的变量会挂载在window上，而let和const声明的变量不会
  var声明变量存在变量提升，let和const不存在变量提升
  let和const声明形成块作用域
  同一作用域下let和const不能声明同名变量，而var可以

- async/await

	- async/await的优势在于处理 then 的调用链，能够更清晰准确的写出代码，并且也能优雅地解决回调地狱问题。当然也存在一些缺点，因为 await 将异步代码改造成了同步代码，如果多个异步代码没有依赖性却使用了 await 会导致性能上的降低。

- class

	-   JavaScript没有真正的类，一直也是通过函数加原型的形式来模拟，class也不例外，只是语法糖，本质还是函数。需要先声明再使用，内部的方法不会被遍历，且没有函数的prototype属性。不过相较ES6之前无论是定义还是继承都好理解了很多。继承主要是使用extends和super关键字，本质类似于ES5的寄生组合继承

	  class Parent {
	      constructor(name) {
	        this.name = name;
	      }
	    }
	    class Child extends Parent {
	      constructor(name, age) {
	        super(name);  // 相当于Parent.call(this, name)
	        this.age = age;
	      }
	    }

- ES-Module

	- 通过import来引入模块，通过export default或export来导出模块

- Proxy

  和Object.defineProperty有些类似，它的作用是用来自定义对象中操作。Proxy的构造函数接受两个参数，第一个参数是需要代理的对象，第二个参数是一个对象，里面会定义get和set方法，当代理对象中的某个值被访问或重新赋值就会触发相应的get和set方法。vue3.0就抛弃了Object.defineProperty而拥抱了Proxy，它的优点是只需要代理一次，对象内的值发生了改变就会被感知到，不再需要像以前为对象的每个值进行数据劫持；而且以前对象的新增，数组的下标设置0清空等情况都可以被感知到，在响应式里也不在需要为数组和对象收集两次依赖，相信会大大提升性能。

### ajax

- 手写

  //1：创建Ajax对象
  var xhr = window.XMLHttpRequest?new XMLHttpRequest():new ActiveXObject('Microsoft.XMLHTTP');// 兼容IE6及以下版本
  //2：配置 Ajax请求地址
  xhr.open('get','index.xml',true);
  //3：发送请求
  xhr.send(null); // 严谨写法
  //4:监听请求，接受响应
  xhr.onreadysatechange=function(){
     if(xhr.readySates==4&&xhr.status==200 || xhr.status==304 )
       console.log(xhr.responsetXML)
  }

- promise 封装

  // promise 封装实现：
  
  function getJSON(url) {
   // 创建一个 promise 对象
   let promise = new Promise(function(resolve, reject) {
    let xhr = new XMLHttpRequest();
  
    // 新建一个 http 请求
    xhr.open("GET", url, true);
  
    // 设置状态的监听函数
    xhr.onreadystatechange = function() {
     if (this.readyState !== 4) return;
  
     // 当请求成功或失败时，改变 promise 的状态
     if (this.status === 200) {
      resolve(this.response);
     } else {
      reject(new Error(this.statusText));
     }
    };
  
    // 设置错误监听函数
    xhr.onerror = function() {
     reject(new Error(this.statusText));
    };
  
    // 设置响应的数据类型
    xhr.responseType = "json";
  
    // 设置请求头信息
    xhr.setRequestHeader("Accept", "application/json");
  
    // 发送 http 请求
    xhr.send(null);
   });
  
   return promise;
  }

- 跨域

	- 概念

		- 浏览器的同源策略
		- 协议、域名、端口有一个不同就算是跨域
		- 防止CSRF攻击，防止利用户的登录状态发起恶意请求

	- 解决跨域

		- JSONP

			- 利用script标签不受同源策略限制

		- CORS

			- 使用自定义的HTTP头部让浏览器和服务器进行沟通，实现CORS的关键是后端，服务端设置Access-Control-Allow-Origin就可以开启，表示哪些域名可以访问资源。

		- 反向代理

			- nginx

			  server {
			          listen       80;
			          server_name  localhost;
			          ## 用户访问 localhost，则反向代理到https://api.shanbay.com
			          location / {
			              root   html;
			              index  index.html index.htm;
			              proxy_pass https://api.shanbay.com;
			          }
			  }

			- node

			  devServer: {
			    contentBase: __dirname + "/",
			    port: 9000,
			    proxy: {
			     "/users": {  //需要代理的路径
			      target: "http://jsonplaceholder.typicode.com", //需要代理的域名
			      changeOrigin: true //必须配置为true，才能正确代理
			     }
			    }
			  }

### 运行机制

- 运行机制

  同步和异步任务分别进入不同的执行"场所"，同步的进入主线程，异步的进入Event Table并注册函数。
  当指定的事情完成时，Event Table会将这个函数移入Event Queue。
  主线程内的任务执行完毕为空，会去Event Queue读取对应的函数，进入主线程执行。
  上述过程会不断重复，也就是常说的Event Loop(事件循环)。
  
  。

- 同步任务
- 异步任务

	- 微任务（有限执行）

		- Promise.then catch finally、node 中的 process.nextTick 、对 Dom 变化监听的 MutationObserver

	- 宏任务

		- script 脚本的执行、setTimeout ，setInterval ，setImmediate 一类的定时事件，还有如 I/O 操作、UI 渲染

### 深浅拷贝

- 浅拷贝

	- Object.assign() 
	- 拓展运算符...

- 深拷贝

	- JSON.parse(JSON.stringify(object))
	- 基础版

	  const deepCopy = obj => {
	      const target = Array.isArray(obj) ? [] : {}
	      for (const key in obj) {
	        const element = obj[key]
	        target[key] = typeof element === 'object' ? deepCopy(element) : element
	      }
	      return target
	    }

### 柯里化

- 所谓"柯里化"，就是把一个多参数的函数，转化为单参数函数。将一个函数转换为一个新的函数

  // 非柯里化
  function add(x, y) {
      return x + y;
  }
  
  add(1, 2) === 3; // true
  
  // 柯里化
  function addX(y) {
      return function(x) {
          return x + y;
      };
  }
  
  addX(2)(1) == 3; // true

- 题目

	- 请实现plus(1)(2)(3)(4)等于8

	  //方法1：
	    function plus(n) {
	      debugger
	      let sum = n;
	      const _plus = function (n) {
	        sum += n;
	        return _plus;
	      };
	      _plus.toString = function () {
	        return sum;
	      };
	      return _plus;
	    }
	  
	    //方法2：
	    function multi() {
	      const args = [].slice.call(arguments);
	      const fn = function () {
	        const newArgs = args.concat([].slice.call(arguments));
	        return multi.apply(this, newArgs);
	      }
	      fn.toString = function () {
	        return args.reduce(function (a, b) {
	          return a + b;
	        })
	      }
	      return fn;
	    }

### 防抖节流

- 防抖debounce

	- 事件被触发 n 秒后再执行回调

	  const debounce = (fn, wait) => {
	      let timeout = null
	      return () => {
	        if (timeout) clearTimeout(timeout)
	        timeout = setTimeout(fn, wait)
	      }
	    }

- 节流throttle

	- 指规定一个单位时间，在这个单位时间内，只能有一次触发事件的回调函数执行

	  const throttle = (fn, wait) => {
	      let prov = Date.now()
	      return () => {
	        let now = Date.now()
	        if (now - prov > wait) {
	          fn()
	          prov = Date.now()
	        }
	      }
	    }

## 网络

### 请求

- GET
- POST
- PUT
- DELETE
- OPTIONS

### 状态码

- 1XX：信息

	- 100 Continue

		- 继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息

- 2XX：成功

	- 200 OK

		- 正常返回信息

	- 201 Created

		- 请求成功并且服务器创建了新的资源

	- 202 Accepted

		- 服务器已接受请求，但尚未处理

- 3XX：重定向

	- 301 Moved Permanently

		- 请求的网页已永久移动到新位置

	- 302 Found

		- 临时性重定向

	- 303 See Other

		- 临时性重定向，且总是使用 GET 请求新的 URI

	- 304 Not Modified

		- 自从上次请求后，请求的网页未修改过

- 4XX：客户端错误

	- 400 Bad Request

		- 服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求

	- 401 Unauthorized

		- 请求未授权

	- 403 Forbidden

		- 禁止访问

	- 404 Not Found

		- 找不到如何与 URI 相匹配的资源

- 5XX: 服务器错误

	- 500 Internal Server Error

		- 最常见的服务器端错误

	- 503 Service Unavailable

		-  服务器端暂时无法处理请求（可能是过载或维护）

### HTTP

### HTTPS

### DNS

### TCP

### CDN

### 从输入url到页面展示

浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求
服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）
浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）
载入解析到的资源文件，渲染页面，完成

## 设计模式

## TypeSctipt

### 介绍

### 优势

### 数据类型

### 介绍泛型，一般使用地方

### 介绍interface

### d.ts作用

### 如何编译

### namespace/modele

## 安全

### XSS

### CSRF

## 优化

### webpack打包

- loader
- dll
- happypack
- 代码压缩
- tree shaking
- thunk splice
- 图片base64·
- exterals
- 路由懒加载

### 网络

- Gzip
- cdn
- 缓存
- preload/prefetch/懒加载
- ssr

### 代码优化

- loading
- 虚拟列表
- 懒加载

## 工程化

### webpack

- 构建流程
- 5大模块
- 热更新如何实现
- 性能优化
- dll
- tree-shaking

### 发布

- 项目发布流程

## node

## 项目

### 项目1

- 介绍
- 功能点
- 难点

## 构造函数

## 原型

## 实例

