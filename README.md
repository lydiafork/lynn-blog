# 面试题积累
  
    1、多人合作开发项目时如何组织代码？

  > 在实际项目中，如果单纯的按model、view、controllers、template 等文件夹进行分类，等项目做大或者文件复杂后，就会出现混乱。因为不清楚引用关系。
> 在项目中，我们经常会修改或者维护单一的页面或者某个功能模块。如本文所说按功能模块或者页面进行文件组织确实是个不错的方法。
> 同时，也可以两者结合起来：先按项目功能分文件夹，里面再按MVC的架构细分文件夹。
> 每个项目都有一些common之类的功能模块，如果一个功能或者函数，有超过2个以上的页面使用，就将它放于common文件夹。
 
    2、js 如何避免全局污染
```
为何要尽量避免全局变量污染呢？
全局变量减少了js的灵活性，增加了耦合性。
若一个项目是由多人合作完成，全局变量容易造成变量名冲突。
根据垃圾回收机制，一个变量的生命周期的结束要等到不再使用该变量，而全局变量则要到关闭浏览器页面才会被回收，所以及其占用内存。
```
解决方法：
1.使用一个全局变量作为容器，将属性跟方法都添加到该对象上
```
var contain = {};
var contain.fn = function() {
// ....
}
```
2.使用自执行函数
```
(function() {
// ...
})()
```



3、 闭包的作用
> 闭包就是由函数创造的一个词法作用域，里面创建的变量被引用后，可以在这个词法环境之外自由使用。闭包通常用来创建内部变量，使得这些变量不能被外部随意修改，同时又可以通过指定的函数接口来操作
> http://blog.csdn.net/sunlylorn/article/details/6534610

4、 h5新标签

> http://www.jianshu.com/p/b4393e798737

5、 ajax同步和异步的处理

> AJAX中根据async的值不同分为同步（async = false）和异步（async = true）两种执行方式
> $.ajax()的async参数总是设置成true，这标志着在请求开始后，其他代码依然能够执行

6、 了解nodejs吗？
7、 设计一个可复用的button组件

8、 react 无状态组件

> 无状态组件就剩了一个 render 方法，因此也就没有没法实现组件的生命周期方法，例如 componentDidMount, componentWillUnmount 等。
*优点（相比于 class 创建组件）*


- 语法更简洁
占内存更小（class 有 props context _context 等诸多属性），首次 render 的性能更好
- 可以写成无副作用的纯函数
可拓展性更强（函数的 compose，currying 等组合方式，比 class 的 extend/inherit 更灵活）
*缺点*

- 无生命周期函数

一个组件就是一个函数，函数应该是谈不上生命周期的，但是组件却是有生命周期，stateless functions 没有生命周期。当然了，我们其实可以使用 高阶组件 去实现生命周期

- 没有 this

在 stateless functions 中，this 是 undefined，所以是不能使用 this 变量。不过换个角度思考，this 是在运行时随时可以被修改或重新赋值，跟外界环境有着密切的联系，正是不使用this才会让组件变得更纯。
例子：
改写前：
```
class ReactFormLabel extends React.Component {
    constructor() {
        super();
    }
    render() {
        return(
            <label htmlFor={this.props.htmlFor}>{this.props.title}</label>
        )
    }
}
```
改写后： 
```
const ReactFormLabel = (props) => 
    <label htmlFor={props.htmlFor}>{props.title}</label>;
```
9、 js 取并集
10、 纯css实现三角形
*把上、左、右三条边隐藏掉（颜色设为 transparent）*
```
#demo {   width: 0;   height: 0;   border-width: 20px;   border-style: solid;   border-color: transparent transparent red transparent; } 
```
*利用transform属性*
HTML：
```
<div class="message-box">
  <span>我是利用 css transfrom 属性字符实现的</span>
  <div class="triangle-css3 transform ie-transform-filter"></div>
</div>
```
CSS：
```
.message-box {
    position:relative;
    width:240px;
    height:60px;
    line-height:60px;
    background:#E9FBE4;
    box-shadow:1px 2px 3px #E9FBE4;
    border:1px solid #C9E9C0;
    border-radius:4px;
    text-align:center;
    color:#0C7823;
}
.triangle-css3 {
    position:absolute;
    bottom:-8px;
    bottom:-6px;
    left:30px;
    overflow:hidden;
    width:13px;
    height:13px;
    background:#E9FBE4;
    border-bottom:1px solid #C9E9C0;
    border-right:1px solid #C9E9C0;
}
.transform {
    -webkit-transform:rotate(45deg);
    -moz-transform:rotate(45deg);
    -o-transform:rotate(45deg);
    transform:rotate(45deg);
}
/*ie7-9*/
.ie-transform-filter {
    -ms-filter: "progid:DXImageTransform.Microsoft.Matrix(
        M11=0.7071067811865475,
        M12=-0.7071067811865477,
        M21=0.7071067811865477,
        M22=0.7071067811865475,
    SizingMethod='auto expand')";
    filter: progid:DXImageTransform.Microsoft.Matrix(
        M11=0.7071067811865475,
        M12=-0.7071067811865477,
        M21=0.7071067811865477,
        M22=0.7071067811865475,
    SizingMethod='auto expand');
}
```
11、 react 生命周期， componentWillMount的意思， 哪个生命周期调用ajax
12、 ios手机端滑动缓慢

在移动端html中经常出现横向/纵向滚动的效果,但是在iPhone中滚动速度很慢,感觉不流畅,有种卡卡的感觉,但是在安卓设备上没有这种感觉;

```
-webkit-overflow-scrolling : touch;
```
13、 手机端禁止缩放
```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no" />
```

14、 localstroge存储和取值
```
localStorage.setItem('myCat', 'Tom');
localStorage.removeItem('myCat');
```
15、 canvas绘制长方形
```
//得到画布上下文，上节已讲，在此不多说
function draw() {
canvas = document.getElementById("canvas");
if (canvas.getContext) { //检测浏览器是否兼容
ctx = canvas.getContext("2d"); //你的canvas代码在这里
return ctx;
}
return null;
}

//画矩形

function juXing() {
var canvas = draw();//获得2d绘图上下文共有方法
canvas.fillStyle = "#2E81CE"; //等同于fillStyle="rgba(46,129,206,1)";
canvas.strokeStyle = "red";
canvas.lineWidth = 2;
canvas.fillRect(10, 10, 100, 120); //填充的四个参数(x,y,width,height)
canvas.strokeRect(10, 10, 100, 120); //线的四个参数(x,y,width,height)
}
```
16、 react classComponent 和 function componenet的区别

React Component 有 3 种定义方式，分别是 React.createClass, class 和 Stateless Functional Component。
Stateless Functional Component无this变量， 无生命周期方法

17、 echarts环形双层图？
18、 js创建一个对象做了哪些操作？
19、 js创建一个对象的方式？
     Object模式、
工厂模式、
```
function Person() {
  var o = new Object();
  o.name = 'hanmeimei';
  o.say = function() {
    alert(this.name);
  }
  return o;
}
var person1 = Person();
```
构造函数模式
```
function Person() {
  this.name = 'hanmeimei';
  this.say = function() {
    alert(this.name)
  }
}

var person1 = new Person();
```
原型模式
```
function Person() {}
Person.prototype.name = 'hanmeimei';
Person.prototype.say = function() {
  alert(this.name);
}
Person.prototype.friends = ['lilei'];
var person1 = new Person();
```
及以上的组合模式。

20、 js继承的方式
     
原型链继承，
```
function Animal(){
　　　　this.species = "动物";
　　}
function Cat(name,color){
　　　　this.name = name;
　　　　this.color = color;
　　}
Cat.prototype = new Animal();
　　Cat.prototype.constructor = Cat;
　　var cat1 = new Cat("大毛","黄色");
　　alert(cat1.species); // 动物
```
构造函数继承
```

　　function Cat(name,color){
　　　　Animal.apply(this, arguments);
　　　　this.name = name;
　　　　this.color = color;
　　}
　　var cat1 = new Cat("大毛","黄色");
　　alert(cat1.species); // 动物
```
原型继承
```
function Animal(){}
Animal.prototype.species = '动物';
function Cat(name,color){
　　　　this.name = name;
　　　　this.color = color;
　　}
Cat.prototype = Animal.prototype;
var cat1 = new Cat("大毛","黄色");
alert(cat1.species); // 动物
```
 拷贝继承（深拷贝（jquery的继承方式）、浅拷贝（早期jQuery的继承方式））。
21、 svg和jpg运用的区别

---------------------------------------
2017-08-02

1、 css 实现子块水平垂直居中， 分子块已知宽高和子块未知宽高两种.
    > 固定宽高：
```

      * position: absolute,left: 50%,width:100px;margin-left: -50px;
      * flex

```


2、 实现多语言切换
3、 let const 和 var 的区别
4、 css 实现动画移动
```
div
{
width:100px;
height:100px;
background:red;
position:relative;
animation:mymove 5s infinite;
-webkit-animation:mymove 5s infinite; /*Safari and Chrome*/
}

@keyframes mymove
{
0% {left:0px; top: 0;}
25% {left:200px; top: 0;}
50% {left:200px; top: 200px;}
75% {left:0px; top: 200px;}
100% {left:0; top: 0;}
}

@-webkit-keyframes mymove /*Safari and Chrome*/
{
0% {left:0px; top: 0;}
25% {left:200px; top: 0;}
50% {left:200px; top: 200px;}
75% {left:0px; top: 200px;}
100% {left:0; top: 0;}
}
```
5、 js 实现冒泡排序
6、 js 实现任意字符串判断是否为ipv4地址
7、 react 生命周期
getDefaultProps()
getInitialState()
componentWillMount()
render 
componentDidMount()

存在期
componentWillReceiveProps()
shouldComponentUpdate
componentWillUpdate()
render()
componentdidUpdate()

销毁
componentWillUnmount
8、 以下代码是否会报错，为什么
```
const a = { name: 1 };
a.name = 2;
console.log(a.name);
 ```
9、 html中src和href的区别
href标识超文本引用，用在link和a等元素上，href是引用和页面关联，是在当前元素和引用资源之间建立联系，src表示引用资源，表示替换当前元素，用在img，script，iframe上.


10、 jQuery的extend函数
  属性拷贝函数
11、 echarts实现柱状图堆叠（思路）
12、 
 ```
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); 


var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); 

 ```
上述两段代码的输出结果分别是？为什么 ？
10 6

13、 js 冒泡事件和捕获事件的区别
   捕获事件从上到下， 冒泡事件从下到上
14、 react 受控组件和非受控组件

受控组件（Controlled Component）代指那些交由 React 控制并且所有的表单数据统一存放的组件。譬如下面这段代码中 username 变量值并没有存放到 DOM 元素中，而是存放在组件状态数据中。任何时候我们需要改变 username 变量值时，我们应当利用 onChange 事件去调用 setState() 函数进行修改。
 ```
class ControlledForm extends Component {
  state = {
    username: ''
  }
  updateUsername = (e) => {
    this.setState({
      username: e.target.value,
    })
  }
  handleSubmit = () => {
    console.log("Input Value: ", this.state.username);
  }
  render () {
    return (
      <form onSubmit={this.handleSubmit}>
        <input
     	  type='text'
          value={this.state.username}
          onChange={this.updateUsername} 
        />
        <button type='submit'>Submit</button>
      </form>
    )
  }
}
 ```
而非受控组件（Uncontrolled Component）则是由 DOM 存放表单数据，并非存放在 React 组件中。我们可以使用 refs 来操控DOM元素，或者通过 id 来获取表单值
 ```
class UnControlledForm extends Component {
  handleSubmit = () => {
    console.log("Input Value: ", this.input.value)
  }
  render () {
    return (
      <form onSubmit={this.handleSubmit}>
        <input
          type='text'
          ref={(input) => this.input = input} 
        />
        <button type='submit'>Submit</button>
      </form>
    )
  }
}
 ```


15、 js继承的方式
16、 js 发起一个ajax
 ```
var xhr = new XMLHttpRequest();
xhr.open('PUT', 'myservice/user/1234');
xhr.setRequestHeader('Content-Type', 'application/json');
xhr.onload = function() {
    if (xhr.status === 200) {
        var userInfo = JSON.parse(xhr.responseText);
    }
};
xhr.send(JSON.stringify({
    name: 'John Smith',
    age: 34
}));
 ```
> (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象 (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息 (3)设置响应HTTP请求状态变化的函数 (4)发送HTTP请求 (5)获取异步调用返回的数据 (6)使用JavaScript和DOM实现局部刷新。

17、 原型链继承的时候call 和 bind 和 apply的区别
call和apply都是对函数的直接调用，而bind方法返回的仍然是一个函数
call 和 apply 是为了动态改变 this 而出现的，对于 apply、call 二者而言，作用完全一样，只是接受参数的方式不太一样。

18、 react在哪个生命周期发起ajax请求
> 我们应当将AJAX 请求放到 componentDidMount 函数中执行，主要原因有下：
> React 下一代调和算法 Fiber 会通过开始或停止渲染的方式优化应用性能，其会影响到 componentWillMount 的触发次数。对于 componentWillMount 这个生命周期函数的调用次数会变得不确定，React 可能会多次频繁调用 componentWillMount。如果我们将 AJAX 请求放到 componentWillMount 函数中，那么显而易见其会被触发多次，自然也就不是好的选择。
> 如果我们将 AJAX 请求放置在生命周期的其他函数中，我们并不能保证请求仅在组件挂载完毕后才会要求响应。如果我们的数据请求在组件挂载之前就完成，并且调用了 setState() 函数将数据添加到组件状态中，对于未挂载的组件则会报错。而在 componentDidMount 函数中进行 AJAX 请求则能有效避免这个问题。


19、 js事件委托
行为委托的实质就是将子元素事件的处理委托给父级元素处理
20、 fis3 和 webpack 区别
21、  Jquery中的bind(),live(),delegate(),on()的区别
http://www.cnblogs.com/moonreplace/archive/2012/10/09/2717136.html
---------------------------------------
2017-08-08

1、 jquery实现图片轮播的原理
2、 对前端工程师这个岗位怎么看
3、 用过什么es6语法
4、 10个div块，jquery实现所有div块变成同一个颜色？ 不同的颜色
5、 jquery常用的函数
6、 react native 项目Android和ios端怎么兼容
7、 为什么用react框架
8、 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么
> 浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求；     服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）；     浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）；     载入解析到的资源文件，渲染页面，完成

---------------------------------------

2017-08-14

1、 HTTP2.0和HTTP1.x的区别？
   二进制协议； 多工； 数据包不按顺序发送，需做标记；头信息压缩； 允许服务器未经请求，主动向客户端发送资源，这叫做服务器推送
  http://www.ruanyifeng.com/blog/2016/08/http.html

2、 HTTP协议中etag的作用?
   实体标签（Entity Tag,ETag）是Web服务器和浏览器用于确认缓存组件的有效性的一种机制
3、 web性能优化
   减少http请求；（css雪碧图， 合并脚本和样式表）
   使用cdn（Content Delivery Network,内容分发网络）
   添加Expire/Cache-Control 头
   启用Gzip压缩
   将css放在页面最上面， js放在页面最下面
   避免 CSS 表达式
   把javascript和css都放到外部文件中
   减少dns请求
   压缩 JavaScript 和 CSS
   避免重定向
   移除重复的脚本
   配置实体标签
   使用ajax缓存

---------------------------------------
2017-08-16

1、 jQuery链式调用

2、 react native 技术点
3、 webpack理解

4、 对Generator函数的理解

5、 flex理解? flex实现bootstrap的栅格化布局

6、 函数式编程
    函数可以作为参数，需要返回值，函数要独立， 不能修改外部变量的值， 闭包

---------------------------------------

2017-08-16
1、 下列代码打印出的结果是
 ```

function Tree() {}
Tree.prototype.oneleafmore = function() {
  this.leaf ++;
  console.log(this.leaf + 'leaves')
};
Tree.prototype.leaf = 0;

const tree1 = new Tree();
tree1.oneleafmore();
tree1.oneleafmore();

const tree2 = new Tree();
tree2.oneleafmore();
 ```
2、 实现AppleTree继承Tree();
 ```
 function AppleTree() {
}
 ```

3、 用户在10s内点击3次， 输出结果是
 ```

function wait() {
  const ms = 10000 + new Date().getTime();
  while (new Date().getTime > ms) {}
  console.log('wait finshed');
  
}
function handleClick() {
  console.log('click');
}
document.addEventListener('click', handleClick);
wait();
console.log('all finished!')
 ```

4 、下列代码的输出结果
 ```
function b() {
  console.log(myvar2);
  console.log(myvar3);

}
function a() {
  var myvar2 = 2;
  var myvar3 = 3;
  b();
}
var myvar1 = 1;
a();
console.log(myvar2);
 ```

5、 下列代码的输出结果
```
for (var i = 1; i <= 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 0);
}
```
6、 100000个排序获取最高的10个数

http://www.10tiao.com/html/564/201604/2650207959/2.html

-20170822———————————————————

1、 css position 的值有哪些？ 分别什么
static （默认值， 表示没有定位）
Absolute（绝对定位） 它不是相对于视窗而是相对于最近的“positioned”祖先元素。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，那么它是相对于文档的 body 元素，
relative(相对定位）
fixed(固定定位） 相对于视窗定位， 元素会相对于视窗来定位，这意味着即便页面滚动，它还是会停留在相同的位置。和 relative 一样， top 、 right 、 bottom 和 left 属性都可用
2、 css 块级元素和行内元素的区别
3、 浮动元素是什么？ 如何清除浮动？
> 浮动可以理解为让某个div元素脱离标准流，漂浮在标准流之上，和标准流不是一个层次。


