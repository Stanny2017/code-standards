# code-standards

This repository contains the specifications.


- [Javascript编码规范](javascript-style-guide.md) <span class="std-rec">[1.3]</span>
- [Javascript编码规范 - ESNext补充篇](es-next-style-guide.md) <span class="std-rec">[draft]</span>
- [HTML编码规范](html-style-guide.md) <span class="std-rec">[1.2]</span>
- [CSS编码规范](css-style-guide.md) <span class="std-rec">[1.2]</span>
- [Less编码规范](less-code-style.md) <span class="std-rec">[1.1]</span>
- [E-JSON数据传输标准](e-json.md) <span class="std-rec">[1.0]</span>
- [模块和加载器规范](module.md) <span class="std-rec">[1.1]</span>
- [包结构规范](package.md) <span class="std-rec">[1.1]</span>
- [项目目录结构规范](directory.md) <span class="std-rec">[1.1]</span>
- [图表库标准](chart.md) <span class="std-rec">[1.0]</span>
- [react编码规范](react-style-guide.md) <span class="std-rec">[draft]</span>

## standards in lianjia

Q：如何养成良好的编码习惯？

A：我代码里写出的每个单词都是经过灵魂拷问的。 

### 目录和文件命名规范

大原则：
- 组件目录和组件文件都是大写（components目录除外）
- 其他目录和文件小写
- 组件目录和组件文件都是大写 components目录名小写
- services,utils目录和文件小写
- index文件和样式文件小写
- models中目录名大写，文件名小写
 
### 代码命名规范

- 大原则：语义化，能使用约定俗称的就用约定俗称的命名

比如js中  response，request,  xxxData, xxxList , xxxDetail,  temp,  xxxArr , xxxObj , userInfo ...   一般都是名词命名

function:根据业务功能  getXXX , updateXXX, changeXXX, saveXXX, deleteXXX, openXXX, closeXXX, getXXXs... 一般都是动词命名

比如css中  header, footer, content,  nav , container ,  wrapper ...

1. js命名规范：

变量名驼峰命名  getListData = () =>{};    const listData = [];

常量名大写，下划线分割：const OPEN_STATUS = "open";

2. css命名规范：

css样式名 全小写！！多词采用 “-“连接；

通用的样式名使用功能语义化样式，比如   .nav    .select 

业务样式名使用业务语义化样式，比如 .user-name  .login-btn

 

### 代码风格规范

js:

1. tab：html,js,css代码的 缩进值4

2. 分号：js代码行末尾使用分号；

3. addEventListner 成对出现

4. 不允许使用 == 只能用 === 

5. js 使用字符串使用单引号 ‘’


css:

1. 避免使用内联样式,计算的动态样式除外

2. 慎重使用 !important


html:

1. 属性值用双引号包裹 “”

2. id使用 全小写 下划线连接  id="xxx_input"


### react 项目中


js:

0. 慎用react的ref,如果用，使用回调函数的方式   
```javascript

<MyInput  ref={(r) => this.emailInput = r;}

                 value={inputValue}

                 onChange={this.onEailInputChange}

 />
 ```

1. props,state值的获取放在第一行,不允许在一个方法中到处使用this.props或者this.state

`const {a,b,c} = this.props; `

在类中，显式声明所有用到的state;

2. 组件有多个props,需要多行垂直排版，如0中所示

3. 组件没有child, 使用闭合标签的形式。 如0中所示，不应写 <MyInput {...props}></MyInput>,并且 /> 要另起一行

4. 使用三目运算符，或者&&来进行显示隐藏判断，不提倡使用className或者style来控制显示隐藏（虽然这样做是正确的）

5. import 全部放在头部,一个包中一如多个变量使用 import {a,b,c} from 'letters';

6. dva的dispatch action尽量不使用传递callback的形式,因为dva中dispatch支持promise,可以直接，如果dispatch effects并且在成功和失败需要不同的处理时，可以用callback.

```javascript
dispatch({type:'TEST',payload:{}}).then(() =>{

     // your "callback" code

})
```

7. 核心逻辑块开始的时候，多加一行空格，并且写注释

8. 修改全局的东西，和其他成员商量

9. 注意dva reduxRouter 的push,replace方法的区别。

10. 组件命名和文件名保持一致，并且不能都叫  App

11. 组件class 内部方法排序，先构造函数，除了render以外生命周期函数，自定义函数（箭头函数的声明方式，必须有注释），render ； render 是组件的最后一个方法

css:

1. 除了公共样式文件外，每个less文件中必须只有一个一级样式名，也就是每个界面都需要有唯一的样式名标识

 

五、中间层规范

1. bucky的action的路径和rd给的路径原则上保持一致。

 

六、提测的代码

1. 不允许有error

2. 不允许有warning

3. 不允许有debugger, console.log

4. 不允许有非解释型注释。

没有用的代码直接删除；

自己测试用的代码直接删除；

5. 不允许有没有用的文件

比如测试时候写的文件等

6. 不允许有没有引用过的声明

比如 let a = 123;  a 却从来没有用过，不可以的！

或者 import a form 'a' ;  然后a从来没用过。

 

七、逻辑规范

1. 遍历的时候，不允许改变原数组，比如：原来数组的长度



Lint and fix tool：[FECS](http://fecs.baidu.com/)
