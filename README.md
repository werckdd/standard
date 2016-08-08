# 观麦编程规范

规范旨在提高代码可读性，促进团队开发效率，减少维护成本以及自身编码能力的提升。

墙裂推荐使用WebStrome+[eslint-plugin-react](https://github.com/gmfe/eslint-plugin-gm)开发，使用webStrome格式化代码，eslint检测代码，基本可以规范代码的编写了。

- [文件命名](#文件命名)
- [JS](#JS)
- [React](#React)
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

## 文件命名

- 文件夹以模块功能命名，全小写，使用`_`连接单词。
- 文件名同上

## JS

- 常量全大写，用`_`连接单词。
- 变量声明，`let`与`const`。
    * 尽量使用`const`
    * 只有在变量值会改变的情况下使用`let`声明

- 变量名。
   * 类名使用帕斯卡命名法。如：`class SendMessage{ }`
   * 方法名、变量名、属性名推荐使用驼峰命名法，即首字母小写，后面的单词首字母大写。如：`const msg='hello world';`
   * 名称最好能正确描述变量所代表的内容，或者方法所执行的动作，不在意名字的长短，发布会压缩的。如：`const fetchSpus = () => {};`

## React

### 命名原则

- action的方法名须有该模块的前缀。
- actionType的常量须有该模块的前缀。
- reduers的名字须有该模块的前缀。
- 以上如果太长则使用缩写，如服务时间管理`Service_Mission_Manage`缩写是`SMM`。
- react-route的path用小写，`_`连接单词`<Route path="service_mission_manage">`。

### jsx闭合 

无子节点的空标签应自闭合，且留一个空格

```jsx
// bad
<Foo></Foo>

// good
<Foo />
```

### ref

总是使用ref回调

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

用Class来定义组件

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

- 属性用双引号`"`，方便这种写法`"don't"`，js部分用单引号`'`

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

- 闭合标签换行

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

怎么定义propTypes, defaultProps, contextTypes？

```jsx
class Link extends React.Component {
 ...
}
Link.propTypes = {};
Link.defaultProps = {};
Link.contextTypes = {};
```

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

- 过eslint检测
- 格式化代码，WebStorm可设置commit的时候自动格式化代码
