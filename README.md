#观麦前端规范

##目录
- [观麦编程规范](#观麦编程规范)
- [观麦git工作流规范](#观麦git工作流规范)



#观麦编程规范

规范旨在提高代码可读性，促进团队开发效率，减少维护成本以及自身编码能力的提升。

墙裂推荐使用WebStrome+[eslint-plugin-react](https://github.com/gmfe/eslint-plugin-gm)开发，使用webStrome格式化代码，eslint检测代码，基本可以规范代码的编写了。

### 说明：

![suggest][Suggest Icon] 表示**建议**，不要求。

## 目录

- [文件命名](#文件命名)
- [JS](#js)
- [React](#react)
    * [命名原则](#命名原则)
    * [jsx闭合](#jsx闭合)
    * [ref](#ref)
    * [Class vs `React.createClass`](#Class vs `React.createClass`)
    * [方法定义](#方法定义)
    * [jsx属性](#jsx属性)
    * [组件内方法顺序](#组件内方法顺序)
    * [组件静态方法](#组件静态方法)
- [注释](#注释)
- [提交代码](#提交代码)
- [美观](#美观)
- [数据处理](#数据处理)
    * [日期处理](#日期处理)
    * [价格处理](#价格处理)

## 文件命名

- 文件夹以模块功能命名，全小写，使用`_`连接单词。
- 文件名同上。

## JS

- 常量全大写，用`_`连接单词。
- 变量声明，`let`与`const`。
    * 尽量使用`const`。
    * 只有在变量值会改变的情况下使用`let`声明。

- 变量名
   * 类名使用帕斯卡命名法。如：`class SendMessage{ }`。
   * 方法名、变量名、属性名推荐使用驼峰命名法，即首字母小写，后面的单词首字母大写。如：`const msg='hello world';`。
   * 名称最好能正确描述变量所代表的内容，或者方法所执行的动作，不在意名字的长短，发布会压缩的。如：`const fetchSpus = () => {};`。

- 导出
   * 模块导出要写在文件最后。 且只有一个export语句。

## React

### 命名原则

- action的方法名须有该模块的前缀。
- actionType的常量须有该模块的前缀。
- reduers的名字须有该模块的前缀。
- 以上如果太长则使用缩写，如服务时间管理`Service_Mission_Manage`缩写是`SMM`。
- react-route的path用小写，`_`连接单词`<Route path="service_mission_manage">`。

### jsx闭合

无子节点的空标签应自闭合。闭合标签前可留空格，可不留。

```jsx
// bad
<Foo></Foo>

// good
<Foo/>

// good
<Foo />
```

### ref  

![suggest][Suggest Icon]
总是使用ref回调。

```jsx
// bad
<Foo
    ref="myRef"
/>
// good
<Foo
    ref={ref => {this.myRef = ref;}}
/>
```

### Class vs `React.createClass`

用Class来定义组件。

```jsx
// bad
const Listing = React.createClass({
  // ...
  render() {
    return <div>{this.state.hello}</div>;
  }
});

// good
class Listing extends React.Component {
  // ...
  render() {
    return <div>{this.state.hello}</div>;
  }
}
```

### 方法定义

- 响应事件的方法名是`handleXXXXX`，且在`constructor`中bind this（如果需要）。

```jsx
class Item extends React.Component {
    constructor(props) {
      super(props);
      this.handleClick = ::this.handleClick;
    }

    handleClick() {
      // do stuff
    }

    render() {
      return <div onClick={this.handleClick} />
    }
}
```

### jsx属性

- 属性用双引号`"`，方便这种写法`"don't"`，js部分用单引号`'`。

```jsx
// bad
<Foo bar='bar' />

// good
<Foo bar="bar" />

// bad
<Foo style={{ left: "20px" }} />

// good
<Foo style={{ left: '20px' }} />
```

- 属性如果多(怎样才算多没标准)则换行，如果换行则全部属性换行。

```jsx
// bad
<Foo name="afadf" nickName="adfadf" age="10" city="SZ" country="china"/>

// bad
<Foo name="afadf"
     nickName="adfadf"
     age="10"
     city="SZ"
     country="china"
/>

// good
<Foo
    name="afadf"
    nickName="adfadf"
    age="10"
    city="SZ"
    country="china"
/>
```

### 闭合标签换行

```jsx
// bad
<Foo
  bar="bar"
  baz="baz" />

// good
<Foo
  bar="bar"
  baz="baz"
/>
```

### 组件内方法顺序

![suggest][Suggest Icon]

```jsx
* optional static methods
* constructor
* getChildContext
* componentWillMount
* componentDidMount
* componentWillReceiveProps
* shouldComponentUpdate
* componentWillUpdate
* componentDidUpdate
* componentWillUnmount
* clickHandlers or eventHandlers like onClickSubmit() or onChangeDescription()
* getter methods for render like getSelectReason() or getFooterContent()
* Optional render methods like renderNavigation() or renderProfilePicture()
* render
```

### 组件静态方法

怎么定义propTypes, defaultProps, contextTypes。其位置顺序不要求。

```jsx
class Link extends React.Component {
 ...
}
Link.propTypes = {};
Link.defaultProps = {};
Link.contextTypes = {};
```

### option的值

select包含`全部`的option，其value用`""`

## 注释

- 单行注释独占一行， `//`后跟一个空格。
- 多行注释建议使用多干单行注释。
- 复杂函数前一定添加文档化注释。如：

```javascript
/**
 * 修改锁价规则。2种修改, 一种是在列表页,一种是在详情页
 * @param postData
 * @param index 传人index,表示为列表页的修改
 * @returns {function()}
 */
```

## 提交代码

- 过eslint检测。
- 格式化代码，WebStorm可设置commit的时候自动格式化代码。

## 美观

![suggest][Suggest Icon]

不同代码功能或者块最好有隔行，提高可读性。

```jsx
// bad
import React from 'react';
class Demo from React.Component{
    xxxx
}
export default Demo;

// good
import React from 'react';

class Demo from React.Component{
    xxxx
}

export default Demo;
```

## 数据处理

### 日期处理
使用[moment.js](http://momentjs.com/docs/)进行日期处理

```javascript
moment("12-25-1995", "MM-DD-YYYY");
moment("2010-10-20 4:30", "YYYY-MM-DD HH:mm");
moment().format("dddd, MMMM Do YYYY, h:mm:ss a");
```
### 价格处理
使用[big.js](https://mikemcl.github.io/big.js/)进行价格处理

```javascript
0.1 + 0.2                  // 0.30000000000000004
x = new Big(0.1)
y = x.plus(0.2)            // '0.3'
Big(0.7).plus(x).plus(y)   // '1.1'
```

---
#观麦git工作流规范
Git 作为一个源码管理系统，不可避免涉及到多人协作。
协作必须有一个规范的工作流程，让大家有效地合作，使得项目井井有条地发展下去。
### 说明：

![suggest][Suggest Icon] 表示**建议**，不要求。


## 目录

- [分支命名](#分支命名)


##分支命名

```
分支命名规范(xxxx的命名用下划线连接)：
`master`: 
主分支， 用于跟踪线上分支

`hotfix-xxx_xxx`: 
用于修复bug的分支, 修复好合并至`master`后便可以删除

`feature-xxx_xx_xx`: 
功能需求类分支, 注意要定期同步一下`master`, 分支feature-xxxx应长期保留，用于记录开发历史

`release-xxx_xx`： 
用于提pr的分支，merge至master后便可删除。
```

更多扩展：
- [Git工作流程介绍](http://www.ruanyifeng.com/blog/2015/12/git-workflow.html)
- [Git相关学习资料](https://github.com/xirong/my-git)



[Suggest Icon]: https://rawgit.com/gmfe/standard/master/svg/min-tuijian.svg
