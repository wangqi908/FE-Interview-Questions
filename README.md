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

- 标准盒模型

	- 

- IE 盒子模型 

	- 

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

### 动画

- 最小时间间隔

	- 多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60*1000ms ＝ 16.7ms

### 布局

- float 

	- 优点： 比较简单，兼容性也比较好。只要清除浮动做的好，是没有什么问题的
	- 缺点：浮动元素是脱离文档流，要做清除浮动，这个处理不好的话，会带来很多问题，比如高度塌陷等。

- 绝对布局

	- 优点：很快捷，设置很方便，而且也不容易出问题
	- 缺点：绝对定位是脱离文档流的，意味着下面的所有子元素也会脱离文档流，这就导致了这种方法的有效性和可使用性是比较差的

- flex 布局

	- 优点：简单快捷
	- 缺点：不支持 IE8 及以下

- table布局

	- 优点：实现简单，代码少
	- 缺点：当其中一个单元格高度超出的时候，两侧的单元格也是会跟着一起变高的，而有时候这种效果不是我们想要的。

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

- Typeof

	- typeof 对于基本类型，除了 null 都可以显示正确的类型

	  typeof 1 // 'number'
	    typeof '1' // 'string'
	    typeof undefined // 'undefined'
	    typeof true // 'boolean'
	    typeof Symbol() // 'symbol'
	    typeof b // b 没有声明，但是还会显示 undefined

	- typeof 对于对象，除了函数都会显示 object

	  typeof [] // 'object'
	    typeof {} // 'object'
	    typeof console.log // 'function'

	- 对于 null来说，虽然它是基本类型，但是会显示 object

- instanceof
- Object.prototype.toString.call(xx)

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

- 闭包的定义很简单：函数 A 返回了一个函数 B，并且函数 B 中使用了函数 A 的变量，函数 B 就被称为闭包。

	- 

- 循环中使用闭包解决 var 定义函数的问题

	- 

		- 

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

	- 

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
	- appendChild(node) //添加

- 移除

	- removeChild(node)

- 替换

	- replaceChild(new,old)

- 插入

	- insertBefore(new,old)

- 查找

	- getElementById()
	- getElementsByName()
	- getElementsByTagName()
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

		- 首字母大写

			- 

		- 找到下标对应的数字

			- 

- Number 

	- toFixed(x)	把数字转换为字符串，结果的小数点后有指定位数的数字。
	- toString()	把数字转换为字符串，使用指定的基数。
	- 转千分位

		- 

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
	- 转换时间戳

		- 

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

		- 

- var,let和const的区别是什么

  var声明的变量会挂载在window上，而let和const声明的变量不会
  var声明变量存在变量提升，let和const不存在变量提升
  let和const声明形成块作用域
  同一作用域下let和const不能声明同名变量，而var可以

- async/await

	- async/await的优势在于处理 then 的调用链，能够更清晰准确的写出代码，并且也能优雅地解决回调地狱问题。当然也存在一些缺点，因为 await 将异步代码改造成了同步代码，如果多个异步代码没有依赖性却使用了 await 会导致性能上的降低。

- class

	-   JavaScript没有真正的类，一直也是通过函数加原型的形式来模拟，class也不例外，只是语法糖，本质还是函数。需要先声明再使用，内部的方法不会被遍历，且没有函数的prototype属性。不过相较ES6之前无论是定义还是继承都好理解了很多。继承主要是使用extends和super关键字，本质类似于ES5的寄生组合继承

		- 1.类中的构造器不是必须要写的，要对实例进行一些初始化的操作，如添加指定属性时才写。
		- 2.如果A类继承了B类，且A类中写了构造器，那么A类构造器中的super是必须要调用的。
		- 3.类中所定义的方法，都放在了类的原型对象上，供实例去使用。

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

	- 微任务（优先执行）

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

### 纯函数

- 1.	一类特别的函数: 只要是同样的输入(实参)，必定得到同样的输出(返回)
- 2.	必须遵守以下一些约束

	- 1)	不得改写参数数据
	- 2)	不会产生任何副作用，例如网络请求，输入和输出设备
	- 3)	不能调用Date.now()或者Math.random()等不纯的方法  

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

### 【js语句(代码)】与【js表达式】

- 表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方

	- (1). a
	- (2). a+b
	- (3). demo(1)
	- (4). arr.map() 
	- (5). function test () {}

- 语句(代码)

	- (1).if(){}
	- (2).for(){}
	- (3).switch(){case:xxxx}

## 框架

### Vue

- Router

	- 原理

		- hash模式

			- window.location.hash

		- history模式

			- pushState（）
			- replaceState（）

	- 路由的钩子函数

		- beforeEach，afterEach,主要有3个参数to，from，next

			- to：route即将进入的目标路由对象
			- from：route当前导航正要离开的路由
			- next：function一定要调用该方法resolve这个钩子。执行效果依赖next方法的调用参数。可以控制网页的跳转

- Vuex

	- state
	- mutations
	- getters
	- action
	- modules
	- plugins

- 问题

	- 简单实现双向数据绑定

		- 

	- 双向绑定数据的原理

		- 采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调

	- data 为什么必须是函数

		- 每个组件都是 Vue 的实例
		- 组件共享 data 属性，当 data 的值是同一个引用类型的值时，改变其中一个会影响其他

	- Proxy 与 Object.defineProperty 对比

		- Object.defineProperty 虽然已经能够实现双向绑定了，但是他还是有缺陷的。
		- 只能对属性进行数据劫持，所以需要深度遍历整个对象 对于数组不能监听到数据的变化
		- Proxy就没以上的问题，原生支持监听数组变化，并且可以直接对整个对象进行拦截，所以 Vue 也将在下个大版本中使用 Proxy 替换 Object.defineProperty

	- 路由原理

		- hash模式

			- hash("#")

		- history模式

			- pushState（），replaceState（）可以对浏览器历史记录栈进行修改，以及popState事件的监听到状态变更

	- key

		- 渲染项目列表时，key 属性允许 Vue 跟踪每个 Vnode。key 值必须是唯一的。
		- 如果没有使用 key 属性，并且列表的内容发生了改变（例如对列表进行排序），则虚拟 DOM 宁愿使用更新的数据来修补节点，来反映更改，而不是上下移动元素。这是默认模式，非常有效。
		- 当提供唯一的键值 IS 时，将根据对键的更改对元素进行重新排序（并且不使用新数据对它们进行修补），如果删除了 key（例如，删除列表中的项目时），则对应的元素节点也被销毁或删除。

	- 父组件监听子组件的生命周期

		- $emit

		  // Parent.vue
		  <Child @mounted="doSomething"/>
		      
		  // Child.vue
		  mounted() {
		    this.$emit("mounted");
		  }

		- @hook

		  //  Parent.vue
		  <Child @hook:mounted="doSomething" ></Child>
		  
		  doSomething() {
		     console.log('父组件监听到 mounted 钩子函数 ...');
		  },
		  
		  //  Child.vue
		  mounted(){
		     console.log('子组件触发 mounted 钩子函数 ...');
		  },        
		  // 以上输出顺序为：
		  // 子组件触发 mounted 钩子函数 ...
		  // 父组件监听到 mounted 钩子函数 ...

	- 组件中写 name 选项有什么作用

		- 项目使用 keep-alive 时，可搭配组件 name 进行缓存过滤
		- DOM 做递归组件时需要调用自身 name
		- vue-devtools 调试工具里显示的组见名称是由vue中组件name决定的

- 生命周期

	- 
	- 外部监听生命周期函数

		- <child @hook:created="handleChildCreated" />
		- 

- 自定义指令

	- Vue.directive(id,definition)
	- 钩子函数

		- bind

			- 只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化动作。

		- inserted

			- 被绑定元素插入父节点时调用（父节点存在即可调用，不必存在于 document 中）

		- update

	- 钩子函数的参数

		- (el, binding, vnode, oldVnode)

- keep-alive使用

	- keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，避免重新渲染
	- 提供 include 和 exclude 属性，两者都支持字符串或正则表达式， include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的组件都不会被缓存 ，其中 exclude 的优先级比 include 高；
	- 对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated。

### React

- 问题

	- React 中 keys 的作用是什么

		- 简单的说: key是虚拟DOM对象的标识, 在更新显示时key起着极其重要的作用。
		- 详细的说: 当状态中的数据发生变化时，react会根据【新数据】生成【新的虚拟DOM】, 随后React进行【新虚拟DOM】与【旧虚拟DOM】的diff比较

			- a. 旧虚拟DOM中找到了与新虚拟DOM相同的key：

				- (1).若虚拟DOM中内容没变, 直接使用之前的真实DOM
				- (2).若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM

			- b. 旧虚拟DOM中未找到与新虚拟DOM相同的key,根据数据创建新的真实DOM，随后渲染到到页面

		- 用index作为key可能会引发的问题

			- 若对数据进行：逆序添加、逆序删除等破坏顺序操作:会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。
			- 如果结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题。

	- 传入 setState 函数的第二个参数的作用是什么

		- 该函数会在setState函数调用完成并且组件开始重渲染的时候被调用，我们可以用该函数来监听渲染是否完成

	- shouldComponentUpdate 

		- 允许我们手动地判断是否要进行组件更新，根据组件的应用场景设置函数的合理返回值能够帮我们避免不必要的更新

	- redux中间件

		- 中间件提供第三方插件的模式，自定义拦截 action -> reducer 的过程。变为 action -> middlewares -> reducer。这种机制可以让我们改变数据流，实现如异步action ，action 过滤，日志输出，异常报告等功能

			- redux-logger：提供日志输出
			- redux-thunk：处理异步操作

	- 为什么虚拟dom会提高性能

		- 虚拟dom相当于在js和真实dom中间加了一个缓存，利用dom diff算法避免了没有必要的dom操作，从而提高性能
		- 用 JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中
		- 当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异
		- 把2所记录的差异应用到步骤1所构建的真正的DOM树上，视图就更新
		- 

	- diff算法

		- 把树形结构按照层级分解，只比较同级元素
		- 给列表结构的每个单元添加唯一的key属性，方便比较
		- React 只会匹配相同 class 的 component（这里面的class指的是组件的名字）
		- 合并操作，调用 component 的 setState 方法的时候, React 将其标记为 - dirty.到每一个事件循环结束, React 检查所有标记 dirty的 component重新绘制.
		- 选择性子树渲染。开发人员可以重写shouldComponentUpdate提高diff的性能

	- 类组件方法this问题

		- 类中的方法默认开启了局部的严格模式，所以方法中的this为undefined
		- 在constructor里通过bind.(this)绑定

			-         constructor() {
          this.changeWeather = this.changeWeather.bind(this)
        }
			- changeWeather = () => {}

- 组件通信方式

	- 父组件向子组件通信
	- 子组件向父组件通信

- 虚拟DOM

	- 1.本质是Object类型的对象（一般对象）
	- 2.虚拟DOM比较“轻”，真实DOM比较“重”，因为虚拟DOM是React内部在用，无需真实DOM上那么多的属性。
	- 3.虚拟DOM最终会被React转化为真实DOM，呈现在页面上。
	-       var div = {
        tagName: 'ul',
        props: { class: 'list' },
        children: [
          { tagName: 'li', children: ['item1'] },
          { tagName: 'li', children: ['item2'] }
        ]
      }

- jsx语法规则

	- 1.定义虚拟DOM时，不要写引号。
	- 2.标签中混入JS表达式时要用{}。
	- 3.样式的类名指定不要用class，要用className。
	- 4.内联样式，要用style={{key:value}}的形式去写。
	- 5.只有一个根标签
	- 6.标签必须闭合
	- 7.标签首字母

		- 若小写字母开头，则将该标签转为html中同名元素，若html中无该标签对应的同名元素，则报错。
		- 若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错。

- 组件

	- 函数式组件

		- 问题

			- this是undefined，因为babel编译后开启了严格模式

		- 过程

			- 1.React解析组件标签，找到组件。
			- 2.发现组件是使用函数定义的，随后调用该函数，将返回的虚拟DOM转为真实DOM，随后呈现在页面中。

	- 类式组件

		- 问题

			- render是放在哪里的？—— 该组件的原型对象上，供实例使用。
			- render中的this是谁？—— 该组件的实例对象。

		- 过程

			- 1.	React内部会创建组件实例对象
			- 2.	调用render()得到虚拟DOM, 并解析为真实DOM
			- 3.	插入到指定的页面元素内部

	- 组件实例三大属性

		- state

			- 理解

				- 1.	state是组件对象最重要的属性, 值是对象(可以包含多个key-value的组合)
				- 2.	组件被称为"状态机", 通过更新组件的state来更新对应的页面显示(重新渲染组件)

			-  强烈注意

				- 1.	组件中render方法中的this为组件实例对象
				- 2.	组件自定义的方法中this为undefined，如何解决？

					- a)	强制绑定this: 通过函数对象的bind()
					- b)	箭头函数

				- 3.	状态数据，不能直接修改或更新

		- props

			- 理解

				- 1.	每个组件对象都会有props(properties的简写)属性
				- 2.	组件标签的所有属性都保存在props中

			- 作用

				- 1.	通过标签属性从组件外向组件内传递变化的数据
				- 2.	注意: 组件内部不要修改props数据

			- 限制

				- Person.propTypes

					- 

				- Person.defaultProps

					- 

		- refs

			- 组件内的标签可以定义ref属性来标识自己
			- 方式

				- 1.	字符串形式的ref

					- <input ref="input1"/>

				- 2.	回调形式的ref

					- <input ref={(c)=>{this.input1 = c}}

				- 3.	createRef创建ref容器

					- myRef = React.createRef()
<input ref={this.myRef}/>

- 生命周期

	- 理解

		- 1.	组件从创建到死亡它会经历一些特定的阶段
		- 2.	React组件中包含一系列勾子函数(生命周期回调函数), 会在特定的时刻调用。
		- 3.	我们在定义组件时，会在特定的生命周期回调函数中，做特定的工作。

	- 三个阶段（旧）

		- 初始化阶段

			- 1.	constructor()
			- 2.	componentWillMount()
			- 3.	render()
			- 4.	componentDidMount()

		- 更新阶段

			- 1.	shouldComponentUpdate()
			- 2.	componentWillUpdate()
			- 3.	render()
			- 4.	componentDidUpdate()

		- 卸载组件

			- 1.	componentWillUnmount()

	- 三个阶段（新）

		- 初始化阶段

			- 1.	constructor()
			- 2.	getDerivedStateFromProps
			- 3.	render()
			- 4.	componentDidMount()

		-  更新阶段

			- 1.	getDerivedStateFromProps
			- 2.	shouldComponentUpdate()
			- 3.	render()
			- 4.	getSnapshotBeforeUpdate
			- 5.	componentDidUpdate()

		- 卸载组件

			- 1.	componentWillUnmount()

	- 重要的勾子

		- 1.	render
		- 2.	componentDidMount
		- 3.	componentWillUnmount

	- 即将废弃的勾子

		- 1.	componentWillMount
		- 2.	componentWillReceiveProps
		- 3.	componentWillUpdate

- 路由

	- 什么是路由

		- 1.	一个路由就是一个映射关系(key:value)
		- 2.	key为路径, value可能是function或component

	- 内置组件

		- 1.	<BrowserRouter>

			- ReactDOM.render(
	<BrowserRouter>
		<App/>
	</BrowserRouter>,
	document.getElementById('root')
)

		- 2.	<HashRouter>
		- 3.	<Route>

			- <Route path="/home" component={Home}/>

		- 4.	<Redirect>

			- <Redirect to="/about"/>

		- 5.	<Link>
		- 6.	<NavLink>

			- <NavLink activeClassName="test" className="list-group-item" to="/home">Home</NavLink>

		- 7.	<Switch>

			- <Switch>
	<Route path="/about" component={About}/>
	<Route path="/home" component={Home}/>
	<Redirect to="/about"/>
</Switch>

	- 基本使用

		- 1.明确好界面中的导航区、展示区
		- 2.导航区的a标签改为Link标签

			- <Link to="/xxxxx">Demo</Link>

		- 3.展示区写Route标签进行路径的匹配

			- <Route path='/xxxx' component={Demo}/>

		- 4.<App>的最外侧包裹了一个<BrowserRouter>或<HashRouter>

	- 三个固定的属性

		- history

			- go: ƒ go(n)
			- push: ƒ push(path, state)
			- replace: ƒ replace(path, state)

		- location

			- pathname: "/about"
			- search: ""
			- state: undefined

		- match

			- params: {}
			- path: "/about"
			- url: "/about"

	- Switch的使用

		- 1.通常情况下，path和component是一一对应的关系。
		- 2.Switch可以提高路由匹配效率(单一匹配)。

	- 严格匹配与模糊匹配

		- 1.默认使用的是模糊匹配（简单记：【输入的路径】必须包含要【匹配的路径】，且顺序要一致）
		- 2.开启严格匹配：<Route exact={true} path="/about" component={About}/>
		- 3.严格匹配不要随便开启，需要再开，有些时候开启会导致无法继续匹配二级路由

	- Redirect的使用	

		- 一般写在所有路由注册的最下方，当所有路由都无法匹配时，跳转到Redirect指定的路由

	- 嵌套路由

		- 1.注册子路由时要写上父路由的path值
		- 2.路由的匹配是按照注册路由的顺序进行的

	- 传参

		- params参数

			- 路由链接(携带参数)：<Link to='/demo/test/tom/18'}>详情</Link>
			- 注册路由(声明接收)：<Route path="/demo/test/:name/:age" 
			- 接收参数：this.props.match.params

		- search参数

			- 路由链接(携带参数)：<Link to='/demo/test?name=tom&age=18'}>详情</Link>
			- 注册路由(无需声明，正常注册即可)：<Route path="/demo/test" component={Test}/>
			- 接收参数：this.props.location.search

		- state参数

			- 路由链接(携带参数)：<Link to={{pathname:'/demo/test',state:{name:'tom',age:18}}}>详情</Link>
			- 注册路由(无需声明，正常注册即可)：<Route path="/demo/test" component={Test}/>
			- 接收参数：this.props.location.state

	- 编程式路由导航

		- 借助this.prosp.history对象上的API对操作路由跳转、前进、后退

			- this.prosp.history.push()
			- this.prosp.history.replace()
			- this.prosp.history.go()

	- BrowserRouter与HashRouter的区别

		- 底层原理不一样

			- BrowserRouter使用的是H5的history API，不兼容IE9及以下版本
			- HashRouter使用的是URL的哈希值

		- path表现形式不一样

			- BrowserRouter的路径中没有#,例如：localhost:3000/demo/test
			- HashRouter的路径包含#,例如：localhost:3000/#/demo/test

		- 刷新后对路由state参数的影响

			- BrowserRouter没有任何影响，因为state保存在history对象中
			- HashRouter刷新后会导致路由state参数的丢失

- redux

	- 理解

		- 专门用于做状态管理的JS库
		- 集中式管理react应用中多个组件共享的状态

	- 工作流程

		- 

	- 核心概念

		- action

			- 1.	动作的对象
			- 2.	包含2个属性

				- type：标识属性, 值为字符串, 唯一, 必要属性
				- data：数据属性, 值类型任意, 可选属性
				- { type: 'ADD_STUDENT',data:{name: 'tom',age:18} }

		- reducer

			- 1.	用于初始化状态、加工状态
			- 2.	加工时，根据旧的state和action， 产生新的state的纯函数

		- store

			- 1.	将state、action、reducer联系在一起的对象
			- 2.	如何得到此对象?

				- 1)	import {createStore} from 'redux'
2)	import reducer from './reducers'
3)	const store = createStore(reducer)

			- 3.	此对象的功能?

				- 1)	getState(): 得到state
				- 2)	dispatch(action): 分发action, 触发reducer调用, 产生新的state
				- 3)	subscribe(listener): 注册监听, 当产生了新的state时, 自动调用

	- 核心API

		- createstore()

			- 作用：创建包含指定reducer的store对象

		- store对象

			- 1.	作用: redux库最核心的管理对象
			- 2.维护state和reducer
			- 3.	核心方法

				- 1)	getState()
				- 2)	dispatch(action)
				- 3)	subscribe(listener)

			- 4.	具体编码

				- 1)	store.getState()
				- 2)	store.dispatch({type:'INCREMENT', number})
				- 3)	store.subscribe(render)

		-  applyMiddleware()

			- 应用上基于redux的中间件(插件库)

		- combineReducers()

			- 合并多个reducer函数

	- 代码编写

		- src下创建redux文件夹

			- 创建store.js

				- 1).引入redux中的createStore函数，创建一个store
2).createStore调用时要传入一个为其服务的reducer
3).记得暴露store对象

			- 创建reducer.js

				- 1).reducer的本质是一个函数，接收：preState,action，返回加工后的状态
2).reducer有两个作用：初始化状态，加工状态
3).reducer被第一次调用时，是store自动触发的，传递的preState是undefined

			- 创建actionCreator.js

				- 专门用于创建action对象

			- 创建actionTypes

				- 放置容易写错的type值

		- 在index.js中监测store中状态的改变，一旦发生改变重新渲染<App/>

	- 异步

		- redux-thunk

			- 配置在store中
			- 创建action的函数不再返回一般对象，而是一个函数，该函数中写异步任务。

				- 

			- 3).异步任务有结果后，分发一个同步的action去真正操作数据。

- react-redux

	- 概念

		- 1).UI组件:不能使用任何redux的api，只负责页面的呈现、交互等。
		- 2).容器组件：负责和redux通信，将结果交给UI组件。

	- 创建容器组件

		- connect(mapStateToProps,mapDispatchToProps)(UI组件)
		- mapStateToProps:映射状态，返回值是一个对象
		- mapDispatchToProps:映射操作状态的方法，返回值是一个对象

	- 容器组件中的store是靠props传进去的，而不是在容器组件中直接引入

		- <App/>包裹一个<Provider store={store}>

- setState更新状态的2种写法

	- 对象式

		- 

	- 函数式

		- 

- lazyLoad

	- 通过React的lazy函数配合import()函数动态加载路由组件

		- 路由组件代码会被分开打包

			- const Login = lazy(()=>import('@/pages/Login'))

	- 通过<Suspense>指定在加载得到路由打包文件前显示一个自定义loading界面

		- 

- Hooks

	- useState()

		- State Hook让函数组件也可以有state状态, 并进行状态数据的读写操作
		- const [xxx, setXxx] = React.useState(initValue)  
		- 参数: 第一次初始化指定的值在内部作缓存
		- 返回值: 包含2个元素的数组, 第1个为内部当前状态值, 第2个为更新状态值的函数
		- setXxx()2种写法

			- setXxx(newValue): 参数为非函数值, 直接指定新的状态值, 内部用其覆盖原来的状态值
			- setXxx(value => newValue): 参数为函数, 接收原本的状态值, 返回新的状态值, 内部用其覆盖原来的状态值

		- 

	- useEffect()

		- Effect Hook 可以让你在函数组件中执行副作用操作(用于模拟类组件中的生命周期钩子)
		- useEffect(() => { 
  // 在此可以执行任何带副作用操作
  return () => { // 在组件卸载前执行
    // 在此做一些收尾工作, 比如清除定时器/取消订阅等
  }
}, [stateValue]) // 如果指定的是[], 回调函数只会在第一次render()后执行
		- 可以把 useEffect Hook 看做如下三个函数的组合

			- componentDidMount()
			- componentDidUpdate()
			- componentWillUnmount() 

		- 

	- useRef()

		-  Ref Hook可以在函数组件中存储/查找组件内的标签或任意其它数据
		- const refContainer = useRef()
		- 作用:保存标签对象,功能与React.createRef()一样
		- 

- Fragment

	- 可以不用必须有一个真实的DOM根标签了

- 组件优化

	- Component的2个问题 

		- 只要执行setState(),即使不改变状态数据, 组件也会重新render()
		- 只当前组件重新render(), 就会自动重新render子组件 ==> 效率低

	- 解决

		- 办法1

			- 重写shouldComponentUpdate()方法
			- 比较新旧state或props数据, 如果有变化才返回true, 如果没有返回false

		- 办法2:

			- 使用PureComponent
			- PureComponent重写了shouldComponentUpdate(), 只有state或props数据有变化才返回true
			- 注意

				- 只是进行state和props数据的浅比较, 如果只是数据对象内部数据变了, 返回false 
				- 不要直接修改state数据, 而是要产生新数据

- render props/插槽

	- 使用children

		- props: 通过组件标签体传入结构

			- 

	- 使用render

		- props: 通过组件标签属性传入结构, 一般用render函数属性

			- 

- 错误边界

	- 用来捕获后代组件错误，渲染出备用页面
	- 只能捕获后代组件生命周期产生的错误，不能捕获自己组件产生的错误和其他组件在合成事件、定时器中产生的错误
	- 使用方式

		- getDerivedStateFromError配合componentDidCatch

	- 

### 微信小程序

- 登录

	- OpenId 

		- 一个用户对于一个小程序／公众号的标识，开发者可以通过这个标识识别出用户。

	- UnionId 

		- 是一个用户对于同主体微信小程序／公众号／APP的标识，开发者需要在微信开放平台下绑定相同账号的主体。开发者可通过UnionId，实现多个小程序、公众号、甚至APP 之间的数据互通了。

	- wx.login 官方提供的登录能力

		- 获取 code向服务端，服务端拿到 code 调用微信登录凭证校验接口，微信服务器返回 openid 和会话密钥 session_key ，此时开发者服务端便可以利用 openid 生成用户入库，再向小程序客户端返回自定义登录态

	- wx.checkSession校验用户当前的session_key是否有效
	- wx.authorize 提前向用户发起授权请求
	- wx.getUserInfo 获取用户基本信息

### MVVM的理解

- Model 代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑
- View 代表UI 组件，它负责将数据模型转化成UI 展现出来
- ViewModel 监听模型数据的改变和控制视图行为、处理用户交互，简单理解就是一个同步View 和 Model的对象，连接Model和View

## Node

### 单线程

### 非阻塞 I/O

### 中间件

- 功能的封装方式，就是封装在程序中处理http请求的功能
- 中间件有一个next()函数，如果不调用next函数，请求就在这个中间件中终止了

## 设计模式

### 发布订阅

- 

### 代理

- 

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

### babel原理

- ES6、7代码输入 -> babylon进行解析 -> 得到AST（抽象语法树）-> plugin用babel-traverse对AST树进行遍历转译 ->得到新的AST树->用babel-generator通过AST树生成ES5代码

### 模块化

- ES6

	- 

- CommonJS

	- 

- AMD

	- 

## 安全

### XSS跨站脚本攻击

- 往Web页面里插入恶意html标签或者javascript代码

	- 最普遍的做法是转义输入输出的内容，对于引号，尖括号，斜杠进行转义

### CSRF跨站请求伪造

- CSRF 就是利用用户的登录态发起恶意请求

	- Get 请求不对数据进行修改
	- 不让第三方网站访问到用户 Cookie
	- 阻止第三方网站请求接口
	- 请求时附带验证信息，比如验证码或者 token

### SQL注入

- SQL命令插入到Web表单递交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令

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
- 海量数据优化渲染

	- 

### SEO

- 合理的title、description、keywords：搜索对着三项的权重逐个减小，title值强调重点即可；description把页面内容高度概括，不可过分堆砌关键词；keywords列举出重要关键词。
- 语义化的HTML代码，符合W3C规范：语义化代码让搜索引擎容易理解网页
- 重要内容HTML代码放在最前：搜索引擎抓取HTML顺序是从上到下，保证重要内容一定会被抓取
- 重要内容不要用js输出：爬虫不会执行js获取内容
- 少用iframe：搜索引擎不会抓取iframe中的内容
- 非装饰性图片必须加alt
- 提高网站速度：网站速度是搜索引擎排序的一个重要指标
- 前后端分离的项目使用服务端同构渲染，既提高了访问速度，同时重要关键内容首次渲染不通过 js 输出
- 友情链接，好的友情链接可以快速的提高你的网站权重
- 外链，高质量的外链，会给你的网站提高源源不断的权重提升
- 向各大搜索引擎登陆入口提交尚未收录站点
- 层级尽量明了，不过分嵌套层级关系。

## TypeSctipt

### 介绍

- TypeScript 并不是一个完全新的语言, 它是 JavaScript 的超集，为 JavaScript 的生态增加了类型机制，并最终将代码编译为纯粹的 JavaScript 代码。

### 优势

- 清楚你的实例来自于哪个类，这个类继承了什么类。
- 编辑器友好，轻松点出实例的所有方法或者类的静态方法。
- 让你的代码更严谨，该传参传参，该为null时判断null，增加你发现bug的概率。
- 定义对象规范，这个对象啥用，啥属性，看interface就够了。

### 数据类型

- String

	- 一个保存字符串的文本，类型声明为 string。可以发现类型声明可大写也可小写，后文同理。
	- let name: string = 'muyy'
	- let name2: String = 'muyy'

- Boolen

	- boolean 是 true 或 false 的值，所以 let isBool3: boolean = new Boolean(1) 就会编译报错，因为 new Boolean(1) 生成的是一个 Bool 对象。
	- let isBool1: boolean = false

- Number

	- let number: number = 10;

- Array

	- 组是 Array 类型。然而，因为数组是一个集合，我们还需要指定在数组中的元素的类型。我们通过 Array<type> or type[] 语法为数组内的元素指定类型
	- let arr:number[] = [1, 2, 3, 4, 5];
	- let arr2:Array<number> = [1, 2, 3, 4, 5];
	- let arr3:string[] = ["1","2"];
	- let arr4:Array<string> = ["1","2"];

- Tuple 

	- Tuple 类型相对于 Array 类型, 其允许元素的类型不一定相同
	- let x: [string, number]
	- x = ['a', 1]

- Enums 

	- 列出所有可用值，一个枚举的默认初始值是 0。一开始的范围可以作如下调整:
	- enum Role {Employee = 3, Manager, Admin}
	- let role: Role = Role.Employee
	- console.log(role) // 3
	- console.log(Role[4]) // Manager

- Any 

	- any 是默认的类型，其类型的变量允许任何类型的值：
	- let notSure:any = 10;
	- let notSure2:any[] = [1,"2",false];

- Void 

	- JavaScript 没有空值 Void 的概念，在 TypeScirpt 中，可以用 void 表示没有任何返回值的函数：
	- function alertName(): void {
  console.log('My name is muyy')
}

- Unknow 

	- 任何使用 any 类型的地方推荐使用 unknow 类型代替它。

- Never 

	- 当函数 throw 或者返回错误, 循环永远为 true 时可以声明为 never 类型。

### 函数

- 为函数定义类型

  function add(x: string, y: string): string {
      return "Hello TypeScript";
    }
  
    let add2 = function (x: string, y: string): string {
      return "Hello TypeScript";
    }
  
    let add3: (x: string, y: string) => string = function (x: string, y: string): string {
      return "Hello TypeScript";
    }

- 可选参数和默认参数

  function buildName(firstName: string, lastname?: string) {
      console.log(lastname ? firstName + "" + lastname : firstName)
    }
  
    let res1 = buildName("鸣", "人"); // 鸣人
    let res2 = buildName("鸣"); // 鸣
    let res3 = buildName("鸣", "人", "君"); // Supplied parameters do not match any signature of call target.

### 类

- 类

  class Person {
      name: string; // 这个是对后文this.name类型的定义
      age: number;
      constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
      }
      print() {
        return this.name + this.age;
      }
    }
  
    let person: Person = new Person('muyy', 23)
    console.log(person.print()) // muyy23

- 继承

  class Person {
      public name: string;  // public、private、static 是 typescript 中的类访问修饰符
      age: number;
      constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
      }
      tell() {
        console.log(this.name + this.age);
      }
    }
  
    class Student extends Person {
      gender: string;
      constructor(gender: string) {
        super("muyy", 23);
        this.gender = gender;
      }
      tell() {
        console.log(this.name + this.age + this.gender);
      }
    }
  
    var student = new Student("male");
    student.tell();  // muyy23male

### 接口

interface LabelValue{
    label: string;
}

function printLabel(labelObj: LabelValue){
    console.log(labelObj.label);
}

let myObj = {
    "label":"hello Interface"
};
printLabel(myObj);

### 修饰符

-  public 

	-  公共默认为 public

- private 

	- 不能在声明它的类的外部访问

- protected 

	- 成员在派生类中仍然可以访问。

### 介绍泛型，一般使用地方

### 介绍interface

### d.ts作用

### 如何编译

### namespace/modele

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

- 三次握手
- 四次挥手

### CDN

### 从输入url到页面展示

浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求
服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）
浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）
载入解析到的资源文件，渲染页面，完成

- 

## 浏览器

### 浏览器缓存

- 强缓存

	- 实现强缓存可以通过两种响应头实现：Expires 和 Cache-Control 。强缓存表示在缓存期间不需要请求，state code 为 200

- 协商缓存

	- 如果缓存过期了，我们就可以使用协商缓存来解决问题。协商缓存需要请求，如果缓存有效会返回 304。
	- 协商缓存需要客户端和服务端共同实现，和强缓存一样，也有两种实现方式

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

	- 如果一个节点中的子节点是动态生成的，那么子节点需要注册事件的话应该注册在父节点上

		- 

- 鼠标事件

	- onmouseover、onmouseout

		- 支持事件冒泡

	- onmouseenter、onmouseleave

- 事件对象

  这个对象里面存放着触发事件的状态，如触发事件的当前元素，键盘事件是哪个按键触发的，滚动事件的位置等等

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

### 渲染机制

- 处理 HTML 并构建 DOM 树
- 处理 CSS 构建 CSSOM 树
- 将 DOM 与 CSSOM 合并成一个渲染树
- 根据渲染树来布局，计算每个节点的位置
- 调用 GPU 绘制，合成图层，显示在屏幕上

## 项目

### 项目1

- 介绍
- 功能点
- 难点

## 算法

### 冒泡排序

- 

### 快速排序

- 

### 递归

- 年龄一个比一个大2岁

	- 

### 斐波那契

- 

### 有一堆整数，请把他们分成三份，确保每一份和尽量相等

- 

### 实现 lodash 的_.get

- 

### 手写数组转树

- 

## 构造函数

## 原型

## 实例

