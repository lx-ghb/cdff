# DOM

##    注册事件



* 点击事件 onclick

* 有光标的时候 onfocus

* 失去焦点时 onblur

* 多次注册事件 .addEventListenter('click',function() {

  * 例 btn.addEventListenter('click',function() {      });

* 鼠标的按键点下的时候触发 onmousedown

  * 例document.onmousemove = function(e) {   }

  * 例box.addEventListener("mouseup", function() {

    ​    console.log(3);

      });

* 鼠标在某个元素身上移动的时候触发 onmousemove

* 鼠标的按键被松开的时候触发 onmouseup

##### 键盘事件onkeydown、onkeyup

```js
- 按键按下：keydown
- 按键弹起：keyup
text.onkeydown = function(e) {
   // console.log(e.keyCode, e.ctrlKey);
    // 判断是否同时按下ctrl和回车
    if (e.ctrlKey && e.keyCode === 13) {
    }
}
```

##### 鼠标移入，移出onmouseover、onmouseout

```js
box.onmouseover = function() {
    // 获取自定义属性
    this.getAttribute("index");
    // 添加节点对象属性，随便添加；
    console.log(this.a);
}

// 鼠标移除时触发
dom.onmouseout = function(){ 
}
```

##### 动画结束事件,帧动画结束事件

```js
//过渡结束时触发
var box = document.querySelector('.box');
box.addEventListener('transitionend',function(){
  console.log(123);
});
//帧动画结束时触发
var box = document.querySelector('.box');
box.addEventListener('animationend',function(){
  console.log(123);
})
```

* 注意：
  - 不能使用on的方式注册，只能使用addEventListener的方式注册
  - 如果帧动画是无限次的，不会触发该事件animationend





##    获取元素对象（DOM节点）

#####       根据DOM节点 获取 DOM节点

```js
父元素.children  //获取子元素：可以得到某个元素之下的所有的子元素的集合，一个**伪数组
元素.parentNode //获取父元素：返回一个；
元素.nextElementSibling  -  得到下一个兄弟元素
元素.previousElementSibling - 得到上一个兄弟元素
```



- 获取元素对象 选择器 !!!

```js
document.querySelector(css选择器);
// 作用：根据选择器获取所有满足条件的元素，这个使用的比较多；
// 参数：多个css选择器，以逗号隔开，都是字符串
// 返回值：伪数组；for，但是这个伪数组上面有forEach方法
document.querySelectorAll(css选择器1,css选择器2...);
```



- 根据**标签名**获取元素

  ```js
  document.getElementsByTagName(tagname);
  ```

  

- 根据元素**类名**获取元素

  ```js
  document.getElementsByClassName(classname);
  ```

- **元素对象的位置**：获取到的是数值

```js
// 得到的是某个元素距离他的offsetParent元素的水平距离
元素.offsetLeft     元素.offsetTop 
元素的offsetParent// 找到一个有定位的父亲元素进行参考，如果亲生父亲没有定位，会一直往上找，直到找打有定位的父亲，或者body；
```





##    操作属性

##### 修改节点

```js
ul.innerHTML = '<li>狗蛋</li>';   // 元素.innerHTML = '是满足html语法的标签结构';
innerText：获取和设置元素对象（DOM节点）的文本信息；
```

##### 自定义属性

```js
a: 元素.getAttribute(属性名)
// 作用： 根据属性名获取属性值   返回值：返回获取属性的值；
b: 元素.setAttribute(属性名,属性值) 
// 作用：添加或者修改属性的值  参数：都是字符串；
c: 元素.removeAttribute(属性名)
// 作用：删除某个属性
```

##### 标准属性-style

```js
// 获取：只能获取行内样式；
div.style.backgroundColor
// 设置
div.style.backgroundColor = "#fff";
```

##### 标准属性-style

```js
console.log(元素.className); // 正常输出元素的class属性
// 如果要修改类样式,会直接覆盖
box.className = '新的类名';
// 解决：在原来的基础上进行添加类名
box.className += '新的类名';
```

#####  属性 类样式对象-classList

```js
a:  box.classList.add("类名1","类名2"...)；
//add：给元素对象添加一个或者多个类名，不会影响原来的类名
// 参数：多个类名，之间用逗号隔开
b:  box.classList.remove("类名1","类名2"...)
//remove： 给元素删除一个或者多个类名
// 参数：多个类名，可以是多个，多个之间用逗号隔开
c:  box.classList.toggle("类名")
//toggle：切换类名，
// 参数： 要切换的类名
```

##### 鼠标位置属性

```js
// 页面坐标系  -  以body的左上角作为原点
事件对象.pageX
事件对象.pageY

// 可视区域坐标系 - 以浏览器的可视区域的左上角为原点的
// 可视区域：就是元素用来显示内容的区域
事件对象.clientX
事件对象.clientY

// 事件的目标对象，用户点击到谁上面了；用于事件委托；
事件对象.target

// 事件的绑定对象，就是是绑定在哪个DOM节点上 和 this一样
// 前面说的事件源，
e.currentTarget==this -----> true
```











##    方法

##### 插入到列表最前面

``` js
父元素.insertBefore(新的子元素,旧的子元素)
```



##### 删除节点

```js
// 父元素.removeChild(要删除的子元素);
var first = ul.children[0];
// 调用方法，移除
ul.removeChild(first);
```



##### 创建节点

```js
document.createElement('标签名');
// 返回值：一个元素对象 DOM节点；
// 注意：该方法创建的元素，是不会自动进入结构里面的，需要自己手动添加
document.write();//JS基础
```



```js
事件对象.stopPropagation();// 阻止冒泡
事件对象.preventDefault();// 阻止默认行为；

document.oncontextmenu = function(e){
  e.preventDefault();// 页面右键事件 查看右键菜单
}

// 阻止a标签转跳
// 1 把a标签的href属性设置为 javascript:void(0);
// 2 在a标签的点击事件里面，return false;
// 3 使用事件对象.preventDefault();
dom_a.addEventListener('click', function(e) {
    e.preventDefault();
});
```







# Bom

## 属性

##### 获取元素的实际宽度和高度

```js
// 返回值：数值；
元素.offsetWidth// 只能进行获取；元素的实际宽度 
元素.offsetHeight// 元素的实际高度

// 获取和设置
dom.style.width；
```



##### location

```js
// 如果想要使用js进行跳转，只需要 location.href = 新的地址;
location.href = 'http://www.jd.com';
```

##### localStorage和JSON

```js
一、localStorage:
// 存储： 后面的值 前面可以放入任何数据类型，保存后为字符串；
// 注意： 如果存储的是对象之类的复杂类型，需要先把复杂类型转换为的字符串，再存进去；
// 多次对一个键进行赋值，会把前面的值覆盖；
localStorage.setItem(键,值);

// 读取 数据
// 返回：我们存入的的数据的值，返回的是字符串；
localStorage.getItem(键);

// 删除键的值
localStorage.removeItem(键);　　

// 全部清空
localStorage.clear();　

二、JSON
// 将对象转换为json格式的字符串   返回值：一个满足json格式的 字符串
JSON.stringify(对象);

// 将json格式的字符串转换为对象  返回值：依赖于你的json格式字符串，可能返回数组，或者是对象....
JSON.parse(json格式字符串);
```









## 方法

#####  获取dom节点

```js
// Computed：计算后的样式
// 返回值： 当前作用在这个元素身上的所有样式的集合对象  BOM的方法；
// 属性：具体的属性 无论是行内的还是CSS样式设置的，都可以获取到；字符串
var res = window.getComputedStyle(元素对象)；
res.width 
```



#####   方法：onload

```js
window.onload = function(){
    // 想要获取图片的宽高，就需要等待图片加载完成后才执行后面的函数；
}
```

##### 定时器

```js
一次性定时器：
var timer = setTimout(函数,延迟的毫秒数);
// 作用： 延迟一定的毫秒之后，调用函数一次;
// 返回值： 是该定时器的id，id可以用于停止这个定时器
clearTimeout(timer);// 停止一次性的定时器：清除后，就不会执行这个定时器；
永久性定时器：
var timer = setInterval(函数,间隔);
// 作用：阶段的时间执行函数；
// 返回值：就是该定时器的id
clearInterval(timer);// 清除永久定时器


```















