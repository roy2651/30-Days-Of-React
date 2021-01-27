<div align="center">
  <h1> 30 Days Of React: useRef</h1>
</sub>

</div>

[<< 第二十六天](../26_Context/26_context-CN.md) | [第二十八天>>](../28_project/28_project-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_27.jpg)

# useRef

在这个挑战中，我们介绍了如何处理不受控制的输入数据。在本节中，我们将使用useRef钩子获取输入数据或访问React应用程序中的任何DOM元素。

useRef返回一个可变的ref对象，该对象的.current属性已初始化为传递的参数（initialValue）。返回的对象将在组件的整个生存期内持续存在。

在下面的示例中，我们看到如何使用useRef挂钩从DOM树的输入和访问元素中获取数据

## 从输入获取数据

让我们从不受控制的输入元素中获取数据。

```js
import React, { useRef } from 'react'
import ReactDOM from 'react-dom'

const App = (props) => {
  const ref = useRef(null)
  const onClick = () => {
    let value = ref.current.value
    alert(value)
  }
  return (
    <div className='App'>
      <h1>How to use data from uncontrolled input using useRef</h1>
      <input type='text' ref={ref} />
      <br />
      <button onClick={onClick}>Get Input Data</button>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## Focus

使用useRef可以在输入上触发焦点事件。

```js
import React, { useRef } from 'react'
import ReactDOM from 'react-dom'

const App = (props) => {
  const ref = useRef(null)
  const onClick = () => {
    ref.current.focus()
  }
  return (
    <div className='App'>
      <h1>How to focus on input element useRef</h1>
      <input type='text' ref={ref} />
      <br />
      <button onClick={onClick}>Click to Focus on input</button>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 从DOM树获取内容

开发React应用程序时请不要接触DOM，因为React具有使用虚拟DOM操纵DOM的独特方式。以防万一，我们有兴趣从DOM树中获取一些内容，可以使用useRef钩子。参见示例：

```js
import React, { useRef } from 'react'
import ReactDOM from 'react-dom'

const App = (props) => {
  const ref = useRef(null)
  const onClick = () => {
    let content = ref.current.textContent
    alert(content)
    console.log(content)
  }
  return (
    <div className='App'>
      <h1 ref={ref}>How to getting content from the DOM tree</h1>
      <button onClick={onClick}>Getting Content</button>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 访问和样式化DOM元素

我们可以从DOM树中访问元素并设置其样式。请参阅以下示例:

```js
import React, { useRef } from 'react'
import ReactDOM from 'react-dom'

const App = (props) => {
  const ref = useRef(null)
  const onClick = () => {
    ref.current.style.backgroundColor = '#61dbfb'
    ref.current.style.padding = '50px'
    ref.current.style.textAlign = 'center'
  }
  return (
    <div className='App'>
      <h1 ref={ref}>How to style HTML from the DOM tree using useRef</h1>
      <button onClick={onClick}>Style it</button>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement
```

# 练习题

1. 开发以下[应用程序](https://www.30daysofreact.com/day-27/hexadecimal-colors)。该应用程序默认情况下会生成27种十六进制颜色。如果单击生成按钮，它将生成另一种新的27种十六进制颜色

🎉 CONGRATULATIONS ! 🎉

[<< 第二十六天](../26_Context/26_context-CN.md) | [第二十八天>>](../28_project/28_project-CN.md)
