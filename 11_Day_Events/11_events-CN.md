<div align="center">
  <h1> 30 Days Of React: 事件</h1>
</div>

[<< 第十天](../10_React_Project_Folder_Structure/10_react_project_folder_structure-CN.md) | [第十二天 >>](../12_Day_Forms/12_forms-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_8.jpg)

- [事件](#事件)
  - [什么是事件?](#什么是事件)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 事件

## 什么是事件?

事件是软件识别的动作或事件。为了使事件更清晰，让我们使用使用计算机时的日常活动，例如单击按钮，将鼠标悬停在图像上，按下键盘，滚动鼠标滚轮等。在本节中，我们将仅重点介绍鼠标和键盘事件。react文档已经有关于[事件-React中文社区](https://react.docschina.org/docs/handling-events.html)的详细说明。

在React中处理事件与使用纯JavaScript在DOM元素上处理元素非常相似。在React和纯JavaScript中处理事件之间的一些语法差异：

- React事件使用camelCase命名，而不是小写.
- 使用JSX，您可以传递一个函数作为事件处理程序，而不是字符串.

让我们看一些示例以了解事件处理。

HTML中的事件处理

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>30 Days Of React App</title>
  </head>
  <body>
    <button>onclick="greetPeople()">Greet People</button>
    <script>
      const greetPeople = () => {
        alert('Welcome to 30 Days Of React Challenge')
      }
    </script>
  </body>
</html>
```

在React中，它略有不同

```js
import React from 'react'
// if it is functional components
const App = () => {
  const greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge')
  }
  return <button onClick={greetPeople}> </button>
}
```

```js
import React, { Component } from 'react'
// if it is functional components
class App extends Component {
  greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge')
  }
  render() {
    return <button onClick={this.greetPeople}> </button>
  }
}
```

HTML和React事件之间的另一个区别是，您不能返回false来防止React中的默认行为。您必须显式调用preventDefault。例如，对于纯HTML，要防止打开新页面的默认链接行为，您可以编写：

纯HTML

```html
<a href="#" onclick="console.log('The link was clicked.'); return false">
  Click me
</a>
```

但是，在React中可能如下所示：

```js
import React, { Component } from 'react'
// if it is functional components
class App extends Component {
  handleClick = () => {
    alert('Welcome to 30 Days Of React Challenge')
  }
  render() {
    return (
      <a href='#' onClick={this.handleClick}>
        Click me
      </a>
    )
  }
}
```
事件处理是一个非常广泛的主题，在这一挑战中，我们将重点介绍最常见的事件类型。我们可能会使用以下鼠标和键盘事件。 _onMouseMove，onMouseEnter，onMouseLeave，onMouseOut，onClick，onKeyDown，onKeyPress，onKeyUp，onCopy，onCut，onDrag，onChange，onBlur，onInput，onSubmit_

让我们实现更多的鼠标和键盘事件。

```js
// index.js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  state = {
    firstName: '',
    message: '',
    key: '',
  }
  handleClick = (e) => {
    // e gives an event object
    // check the value of e using console.log(e)
    this.setState({
      message: 'Welcome to the world of events',
    })
  }
  // triggered whenever the mouse moves
  handleMouseMove = (e) => {
    this.setState({ message: 'mouse is moving' })
  }
  // to get value when an input field changes a value
  handleChange = (e) => {
    this.setState({
      firstName: e.target.value,
      message: e.target.value,
    })
  }

  // to get keyboard key code when an input field is pressed
  // it works with input and textarea
  handleKeyPress = (e) => {
    this.setState({
      message:
        `${e.target.value} has been pressed and the keycode is` + e.charCode,
    })
  }
  // Blurring happens when a mouse leave an input field
  handleBlur = (e) => {
    this.setState({ message: 'Input field has been blurred' })
  }
  // This event triggers during a text copy
  handleCopy = (e) => {
    this.setState({
      message: 'Using 30 Days Of React for commercial purpose is not allowed',
    })
  }
  render() {
    return (
      <div>
        <h1>Welcome to the World of Events</h1>

        <button onClick={this.handleClick}>Click Me</button>
        <button onMouseMove={this.handleMouseMove}>Move mouse on me</button>
        <p onCopy={this.handleCopy}>
          Check copy right permission by copying this text
        </p>

        <p>{this.state.message}</p>
        <label htmlFor=''> Test for onKeyPress Event: </label>
        <input type='text' onKeyPress={this.handleKeyPress} />
        <br />

        <label htmlFor=''> Test for onBlur Event: </label>
        <input type='text' onBlur={this.handleBlur} />

        <form onSubmit={this.handleSubmit}>
          <div>
            <label htmlFor='firstName'>First Name: </label>
            <input
              onChange={this.handleChange}
              name='firstName'
              value={this.state.value}
            />
          </div>

          <div>
            <input type='submit' value='Submit' />
          </div>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

# 练习题

## 练习: Level 1

1. 什么是事件?
2. HTML元素事件和React事件之间有什么区别?
3. 至少写4个键盘事件?
4. 编写至少8个鼠标事件?
5. 最常见的鼠标和键盘事件是什么?
6. 写一个特定于输入元素的事件?
7. 写一个特定于表单元素的事件?
8. 当鼠标在身体上移动时，显示视口的坐标吗?
9. onInput，onChange和onBlur有什么区别?
10. 我们在哪里放置onSubmit事件 ?

## 练习: Level 2

使用onMouseEnter事件实现以下内容

![On mouse enter event](../images/react_event_on_mouse_enter.gif)

## 练习: Level 3

未完待续...

🎉 CONGRATULATIONS ! 🎉

[<< 第十天](../10_React_Project_Folder_Structure/10_react_project_folder_structure-CN.md) | [第十二天 >>](../12_Day_Forms/12_forms-CN.md)
