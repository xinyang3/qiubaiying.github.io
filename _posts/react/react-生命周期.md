##### 周期图

![过程图](./生命周期.png)

##### 概述

react组件的生命周期可以 被分为三个阶段：挂载阶段、更新阶段、卸载阶段

+ 挂载阶段

1、 constructor

props指向的就是组件的默认属性。你必须在这个方法中首先调用 super(props)才能保证props被传入组件中。constructor通常用于初始化组件的state以及绑定事件处理方法等

2、componentWillMount

很少用到，可提前到constructor,调用this.setState不会引起重新渲染

3、render

组件内必须有，返回react元素，进行渲染UI

render并不负责组件的实际渲染工作，它只是返回一个UI的描述，真正 的渲染出页面DOM的工作由React自身负责。render是一个纯函数，在这 个方法中不能执行任何有副作用的操作，所以不能在render中调用 this.setState，这会改变组件的状态

4、componentDidMount

在组件被挂载到DOM后调用，且只会被调用一次，dom已被渲染，可以发起请求,this.setState会重新渲染

+ 更新阶段

无论props是否改变，父组 件render方法每一次调用，都会导致组件更新。State引起的组件更新， 是通过调用this.setState修改组件state来触发的

1、componentWillReceiveProps

props引起的组件更新会调用,需要比较nextProps和this.props 来决定是否执行props发生变化后的逻辑，比如根据新的props调用 this.setState触发组件的重新渲染。<span style="color:red;">需要自己判断？</span>

2、shouldComponentUpdate

这个方法决定组件是否继续执行更新过程。当方法返回true时，组件会继续更新过程；当方法返回false 时，组件的更新过程停止，后续的componentWillUpdate、render、 componentDidUpdate也不会再被调用

3、componentWillUpdate

render前调用，很少用到

4、componentDidUpdate

组件更新后被调用，可以作为操作更新后的DOM的地方

+ 卸载阶段

componentWillUnmount

这个方法在组件被卸载前调用，可以在这里执行一些清理工作，比 如清除组件中使用的定时器，清除componentDidMount中手动创建的 DOM元素等，以避免引起内存泄漏。

##### 新增方法

![生命周期-新增](./imgs/生命周期-新增.png)

##### 参考

[简述-生命周期](https://www.jianshu.com/p/514fe21b9914)

[reaact进阶之路](cap.2.3)
