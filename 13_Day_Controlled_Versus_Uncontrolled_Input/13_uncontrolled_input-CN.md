<div align="center">
  <h1> 30 Days Of React: 非受控组件</h1>
</div>

[<< 第十二天](../12_Day_Forms/12_forms-CN.md) | [第十四天 >>](../14_Day_Component_Life_Cycles/14_component_life_cycles-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_13.jpg)

- [非受控组件](#非受控组件)
  - [从不受控制的输入中获取数据](#从不受控制的输入中获取数据)
  - [从表单获取多个输入数据](#从表单获取多个输入数据)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)

# 非受控组件

在前一天的挑战中，我们介绍了受控输入。 在大多数时候在React中，我们使用React官方文档中建议的受控输入 [非受控组件-中文社区](https://react.docschina.org/docs/uncontrolled-components.html).

要编写不受控制的组件，可以使用ref从DOM获取表单值，而不是为每个状态更新编写事件处理程序。在不受控制的输入中，我们从输入字段（如传统的HTML表单数据处理）中获取数据。

不受控制的组件示例

## 从不受控制的输入中获取数据

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  firstName = React.createRef()

  handleSubmit = (e) => {
    e.preventDefault()
    console.log(this.firstName.current.value)
  }

  render() {
    return (
      <div className='App'>
        <form onSubmit={this.handleSubmit}>
          <label htmlFor='firstName'>First Name: </label>
          <input
            type='text'
            id='firstName'
            name='firstName'
            placeholder='First Name'
            ref={this.firstName}
          />
          <button type='submit'>Submit</button>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 从表单获取多个输入数据

我们可以从DOM中获取多个输入数据。我们不是直接针对DOM，而是React使用ref从DOM获取数据。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  firstName = React.createRef()
  lastName = React.createRef()
  country = React.createRef()
  title = React.createRef()

  handleSubmit = (e) => {
    // stops the default behavior of form element specifically refreshing of page
    e.preventDefault()

    console.log(this.firstName.current.value)
    console.log(this.lastName.current.value)
    console.log(this.title.current.value)
    console.log(this.country.current.value)

    const data = {
      firstName: this.firstName.current.value,
      lastName: this.lastName.current.value,
      title: this.title.current.value,
      country: this.country.current.value,
    }
    // the is the place we connect backend api to send the data to the database
    console.log(data)
  }

  render() {
    return (
      <div className='App'>
        <h3>Add Student</h3>
        <form onSubmit={this.handleSubmit}>
          <div>
            <input
              type='text'
              name='firstName'
              placeholder='First Name'
              ref={this.firstName}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='lastName'
              placeholder='Last Name'
              ref={this.lastName}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='country'
              placeholder='Country'
              ref={this.country}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='title'
              placeholder='Title'
              ref={this.title}
              onChange={this.handleChange}
            />
          </div>

          <button className='btn btn-success'>Submit</button>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

大多数时候，我们使用受控输入而不是非受控输入。如果要在DOM上定位某个元素，则可以使用ref来获取该元素的内容。不要使用纯JavaScript直接触摸。开发React应用程序时，请勿直接接触DOM，因为React具有自己的DOM处理方式。

# 练习题

## 练习: Level 1

1. 什么是受控输入？
2. 什么是不受控制的输入
3. 您如何在React中获取某个HTML元素的内容？
4. 为什么在React中直接触摸DOM并不是一个好主意？ ?
5. 在React中最常用的是什么？受控或不受控制的输入
6. 您需要写什么不受控制的输入？
7. 状态是否需要写入不受控制的输入？
8. 什么时候使用不受控制的输入？
9. 什么时候使用受控输入？
10. 您使用受控输入还是非受控输入来验证表单输入字段？

🎉 CONGRATULATIONS ! 🎉

[<< 第十二天](../12_Day_Forms/12_forms-CN.md) | [第十四天 >>](../14_Day_Component_Life_Cycles/14_component_life_cycles-CN.md)
