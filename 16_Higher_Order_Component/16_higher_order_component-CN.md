<div align="center">
  <h1> 30 Days Of React: 高阶组件</h1>
</div>

[<< 第十五天](../15_Third_Party_Packages/15_third_party_packages-CN.md) | [第十七天 >>](../17_React_Router/17_react_router-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_16.jpg)

- [高阶组件](#高阶组件)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 高阶组件

术语高阶组件类似于JavaScript中的高阶函数。在JavaScript中，高阶函数是将另一个函数作为参数或返回另一个函数的函数。

类似于高阶函数，高阶组件采用一个组件并返回另一个组件。通过示例可以理解该定义。请看下面的示例，以更好地理解。

```js
// One way of writing a Higher Order Component(HOC)
import React from 'react'
const higherOrderComponent = (Component) => {
  return (props) => {
    return <Component {...props} />
  }
}
```

大多数时候，第三方库使用高阶组件。例如redux，react-router-dom和material-u使用高阶组件。

```js
import React from 'react'

const Button = ({ onClick, text, style }) => {
  return (
    <button onClick={onClick} style={style}>
      {text}
    </button>
  )
}

const buttonWithStyle = (CompParam) => {
  const buttonStyles = {
    backgroundColor: '#61dbfb',
    padding: '10px 25px',
    border: 'none',
    borderRadius: 5,
    margin: 3,
    cursor: 'pointer',
    fontSize: 18,
    color: 'white',
  }
  return (props) => {
    return <CompParam {...props} style={buttonStyles} />
  }
}
const NewButton = buttonWithSuperPower(Button)

class App extends Component {
  render() {
    return (
      <div className='App'>
        <Button text='No Style' />
        <NewButton text='Styled Button' />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

让我们使buttonWithStyle的高阶除组件外还接受更多参数。

```js
import React from 'react'

const Button = ({ onClick, text, style }) => {
  return (
    <button onClick={onClick} style={style}>
      {text}
    </button>
  )
}

const buttonWithStyles = (CompParam, name = 'default') => {
  const colors = [
    {
      name: 'default',
      backgroundColor: '#e7e7e7',
      color: '#000000',
    },
    {
      name: 'react',
      backgroundColor: '#61dbfb',
      color: '#ffffff',
    },
    {
      name: 'success',
      backgroundColor: '#4CAF50',
      color: '#ffffff',
    },
    {
      name: 'info',
      backgroundColor: '#2196F3',
      color: '#ffffff',
    },
    {
      name: 'warning',
      backgroundColor: '#ff9800',
      color: '#ffffff',
    },
    {
      name: 'danger',
      backgroundColor: '#f44336',
      color: '#ffffff',
    },
  ]
  const { backgroundColor, color } = colors.find((c) => c.name === name)

  const buttonStyles = {
    backgroundColor,
    padding: '10px 45px',
    border: 'none',
    borderRadius: 3,
    margin: 3,
    cursor: 'pointer',
    fontSize: '1.25rem',
    color,
  }
  return (props) => {
    return <CompParam {...props} style={buttonStyles} />
  }
}

const NewButton = buttonWithSuperPower(Button)
const ReactButton = buttonWithSuperPower(Button, 'react')
const InfoButton = buttonWithSuperPower(Button, 'info')
const SuccessButton = buttonWithSuperPower(Button, 'success')
const WarningButton = buttonWithSuperPower(Button, 'warning')
const DangerButton = buttonWithSuperPower(Button, 'danger')

class App extends Component {
  render() {
    return (
      <div className='App'>
        <Button text='No Style' onClick={() => alert('I am not styled yet')} />
        <NewButton
          text='Styled Button'
          onClick={() => alert('I am the default style')}
        />
        <ReactButton text='React' onClick={() => alert('I have react color')} />
        <InfoButton
          text='Info'
          onClick={() => alert('I am styled with info color')}
        />
        <SuccessButton text='Success' onClick={() => alert('I am successful')} />
        <WarningButton
          text='Warning'
          onClick={() => alert('I warn you many times')}
        />
        <DangerButton
          text='Danger'
          onClick={() => alert('Oh no, you can not restore it')}
        />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

上面的示例是高阶组件的一种使用情况。但是，它的用例不仅仅是样式简单的按钮。它具有大量的用例，它使我们能够重用组件并通过样式和功能增强组件。在接下来的部分中，我们将介绍React Router，我们将使用HOC，当您看到一个组件包装了另一个组件时，您不会感到惊讶。

# 练习题

## 练习: Level 1

1. 什么是高阶函数
2. 什么是高阶组件
3. 阶函数和高阶组件之间有什么区别？
4. 高阶组件可以使我们增强组件. (真 or 假)

## 练习: Level 2

1. 制作一个可以处理所有输入类型的高阶组件。

## 练习: Level 3

敬请期待

🎉 CONGRATULATIONS ! 🎉

[<< 第十五天](../15_Third_Party_Packages/15_third_party_packages-CN.md) | [第十七天 >>](../17_React_Router/17_react_router-CN.md)
