## 小农女JavaScript代码规范
规范旨在提高代码可读性，促进团队开发效率，减少维护成本以及自身编码能力的提升。

强烈推荐使用webStrome+[eslint-plugin-react](https://github.com/gmfe/eslint-plugin-gm)开发，使用webStrome格式化代码，eslint检测代码，基本可以规范代码的编写了。

### js
1. 变量声明。let与const。
    1. 尽量使用const
    2. 只有在变量值会改变的情况下使用let声明

2. 变量名。
   1. 类名使用帕斯卡命名法。如：class SendMessage{ }
   2. 方法名、变量名、属性名推荐使用驼峰命名法，即首字母小写，后面的单词首字母大写。如：`const msg="hello world";`
   3. 名称最好能正确描述变量所代表的内容，或者方法所执行的动作。如：const fetchSpus = () => {};


### React
1. 命名原则。
    1. 文件夹以模块功能命名，可使用`_`连接单词，文件名也一样。
    2. action的方法名须有该模块的前缀。

2. 无子节点的空标签应自闭合。
3. 总是使用ref回掉。

```
// bad
<Foo
        ref="myRef"
/>
// good
<Foo
        ref={ref => { this.myRef = ref; }}
/>
```

4. 组件内方法顺序。

```
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

5. 怎么定义propTypes, defaultProps, contextTypes？

```
class Link extends React.Component {
 ...
}
Link.propTypes = {};
Link.defaultProps = {};
Link.contextTypes = {};
```

### 注释
1. 单行注释独占一行， `//`后跟一个空格。
2. 多行注释建议使用多干单行注释。
3. 复杂函数前一定添加文档化注释。如：

```
/**
 * 修改锁价规则。2种修改, 一种是在列表页,一种是在详情页
 * @param postData
 * @param index 传人index,表示为列表页的修改
 * @returns {function()}
 */
```
