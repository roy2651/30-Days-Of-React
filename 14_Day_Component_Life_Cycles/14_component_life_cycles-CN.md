<div align="center">
  <h1> 30 Days Of React:组件的生命周期</h1>
</div>

[<< 第十三天](../13_Day_Controlled_Versus_Uncontrolled_Input/13_uncontrolled_input-CN.md) | [第十五天 >>](../15_Third_Party_Packages/15_third_party_packages-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_14.jpg)

- [组件的生命周期](#组件的生命周期)
  - [什么是组件的生命周期](#什么是组件的生命周期)
  - [Mounting](#mounting)
    - [Contructor](#contructor)
    - [getDerivedStateFromPros](#getderivedstatefrompros)
    - [Render](#render)
    - [ComponentDidMount](#componentdidmount)
  - [Updating](#updating)
    - [getDerivedStateFromProps](#getderivedstatefromprops)
    - [shouldComponentUpdate](#shouldcomponentupdate)
    - [render](#render-1)
    - [componentDidUpdate](#componentdidupdate)
  - [Unmounting](#unmounting)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 组件的生命周期

## 什么是组件的生命周期

组件生命周期是在React应用程序中安装，更新和销毁组件的过程。您可以将生命周期的组成部分与人类的成长过程相关联：出生，成人，老年人和死亡。在React组件中，组件也可以首次安装或渲染，可以通过更改数据进行更新，也可以在不需要时销毁。在React中，每个组件都有三个主要阶段：

- Mounting
- Updating
- Unmounting

## Mounting

将React组件渲染或放入DOM称为安装。在安装React组件期间，以下内置方法按给定顺序运行。

1. constructor()
2. static getDerivedStateFromProps()
3. render()
4. componentDidMount()

当我们制作基于类的组件时，我们使用了内置的render方法，所有基于类的组件都需要它，但是其他方法是可选的。通过运行以下代码片段，查看不同方法的执行顺序。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: '',
    }
  }

  static getDerivedStateFromProps(props, state) {
    console.log(
      'I am getDerivedStateFromProps and I will be the second to run.'
    )
    return null
  }
  componentDidMount() {
    console.log('I am componentDidMount and I will be last to run.')
  }

  render() {
    console.log('I am render and I will be the third to run.')
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### Contructor

如今，我们编写了不带构造函数的基于类的组件，并且也可以在构造函数之外编写状态。在旧版本的React中，我们使用的状态始终在构造函数内部。

当初始化组件时，constructor()方法在执行任何其他方法之前执行，并且是设置初始状态和其他值的地方。在类中，我们使用构造函数参数从父级继承，而在React中，构造函数采用props参数，并且还必须调用super方法。查看有关构造函数和状态的代码片段。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: '',
    }
  }
  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h2>The constructor is the first to Run</h2>
        <p>Author:{this.state.firstName}</p>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### getDerivedStateFromPros

从名称可以理解，此方法从props导出状态。在DOM中呈现组件之前，将立即调用getDerivedStateFromProps()方法。这是根据初始道具设置状态对象的正确位置。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

const User = ({ firstName }) => (
  <div>
    <h1>{firstName}</h1>
  </div>
)

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    // we can write state inside or outside the constructor
    // if is written outside the constructor it does not need the keyword this
    this.state = {
      firstName: 'John',
    }
  }
  static getDerivedStateFromProps(props, state) {
    console.log(
      'I am getDerivedStateFromProps and I will be the second to run.'
    )
    return { firstName: props.firstName }
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h3>getDerivedStateFromProps</h3>
        <User firstName={this.state.firstName} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App firstName='Asabeneh' />, rootElement)
```

### Render

创建基于类的组件时，render方法是必需的方法。render方法是我们返回JSX的地方。只要状态发生变化，render方法就会进行渲染。不要在render方法中设置状态。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

const User = ({ firstName }) => (
  <div>
    <h1>{firstName}</h1>
  </div>
)

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    // we can write state inside or outside the constructor
    // if is written outside the constructor it does not need the keyword this
    this.state = {
      firstName: 'John',
    }
  }
  render() {
    // Never do this
    // Do not reset inside the render method, create a method to reset the state

    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h3>Render method</h3>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App firstName='Asabeneh' />, rootElement)
```

### ComponentDidMount

正如我们可以理解的那样，在组件渲染后此方法调用的方法的名称。这是设置时间间隔和调用API的地方。查看componentDidMount方法中的以下setTimeout实现。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
    }
  }
  componentDidMount() {
    console.log('I am componentDidMount and I will be last to run.')
    // after 3 seconds it resets the state
    setTimeout(() => {
      this.setState({
        firstName: 'Asabeneh',
      })
    }, 3000)
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h2>componentDidMount Method</h2>
        {this.state.firstName}
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

在上面的代码片段中，我们看到了如何在componentDidMount方法内实现setTimeout。在下一个示例中，我们将使用访存来实现API调用。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
      data: [],
    }
  }

  componentDidMount() {
    console.log('I am componentDidMount and I will be last to run.')
    const API_URL = 'https://restcountries.eu/rest/v2/all'
    fetch(API_URL)
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        console.log(data)
        this.setState({
          data,
        })
      })
      .catch((error) => {
        console.log(error)
      })
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <div>
                <div>
                  {' '}
                  <img src={country.flag} alt={country.name} />{' '}
                </div>
                <div>
                  <h1>{country.name}</h1>
                  <p>Capital: {country.capital}</p>
                  <p>Population: {country.population}</p>
                </div>
              </div>
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

有时最好有一个单独的方法来呈现数据。请参阅以下示例：

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
      data: [],
    }
  }

  componentDidMount() {
    console.log('I am componentDidMount and I will be last to run.')
    const API_URL = 'https://restcountries.eu/rest/v2/all'
    fetch(API_URL)
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        console.log(data)
        this.setState({
          data,
        })
      })
      .catch((error) => {
        console.log(error)
      })
  }
  renderCountries = () => {
    return this.state.data.map((country) => {
      return (
        <div>
          <div>
            {' '}
            <img src={country.flag} alt={country.name} />{' '}
          </div>
          <div>
            <h1>{country.name}</h1>
            <p>Population: {country.population}</p>
          </div>
        </div>
      )
    })
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>{this.renderCountries()}</div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## Updating

在DOM上安装组件之后，可以在状态或道具更改时对其进行更新。React组件的更新可能是由于props或state的更改引起的。重新渲染组件时，将按以下顺序调用这些方法

1. static getDerivedStateFromProps()
2. shouldComponentUpdate()
3. render()
4. getSnapshotBeforeUpdate()
5. componentDidUpdate()

### getDerivedStateFromProps

与mounting阶段相似，也可以在更新阶段调用getDerivedStateFromProps。getDerivedStateFromProps是在更新组件时调用的第一个方法。

### shouldComponentUpdate

内置生命周期方法shouldComponentUpdate()应该返回一个布尔值。如果此方法未返回true，则应用程序将不会更新。

如果该方法未返回true，则应用程序将永远不会更新。例如，当达到某个特定点（游戏，订阅）时，这可以用来阻止使用，或者可以用来阻止某个用户。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
      data: [],
    }
  }

  shouldComponentUpdate(nexProps, nextState) {
    console.log(nextProps, nextState)
    // if the return is true, the application will never update.
    return true
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

例如，如果我们要在30天后停止进行挑战，则可以将日期从1天增加到30天，并且可以在30天时阻止应用程序。请看示例。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
      day: 1,
    }
  }

  shouldComponentUpdate(nextProps, nextState) {
    console.log(nextProps, nextState)
    console.log(nextState.day)
    if (nextState.day > 31) {
      return false
    } else {
      return true
    }
  }
  // the doChallenge increment the day by one
  doChallenge = () => {
    this.setState({
      day: this.state.day + 1,
    })
  }
  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <button onClick={this.doChallenge}>Do Challenge</button>
        <p>Challenge: Day {this.state.day}</p>
        {this.state.congratulate && <h2>{this.state.congratulate}</h2>}
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### render
正如我们在组件的mounting阶段提到的那样，当组件更新时，将调用render()方法。它必须使用新更改将HTML重新呈现到DOM。

### componentDidUpdate

componentDidUpdate方法采用两个参数：prevProps和prevState。在DOM中更新组件后调用它。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      firstName: 'John',
      data: [],
    }
  }
  componentDidUpdate(prevProps, prevState) {
    console.log(prevState, prevProps)
  }
  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

让我们一起使用以上两种生命周期方法。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  constructor(props) {
    super(props)
    console.log('I am  the constructor and  I will be the first to run.')
    this.state = {
      day: 1,
      congratulate: '',
    }
  }

  shouldComponentUpdate(nextProps, nextState) {
    console.log(nextProps, nextState)
    console.log(nextState.day)
    if (nextState.day > 31) {
      return false
    } else {
      return true
    }
  }

  doChallenge = () => {
    this.setState({
      day: this.state.day + 1,
    })
  }
  componentDidUpdate(prevProps, prevState) {
    if (prevState.day == 30) {
      this.setState({
        congratulate: 'Congratulations,Challenge has been completed',
      })
    }
    console.log(prevState, prevProps)
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <button onClick={this.doChallenge}>Do Challenge</button>
        <p>Challenge: Day {this.state.day}</p>
        {this.state.congratulate && <h2>{this.state.congratulate}</h2>}
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## Unmounting
组件生命周期的最后阶段是unmounting。unmounting阶段将从DOM中删除组件。componentWillUnmount方法是卸载组件时唯一调用的内置方法。

# 练习题

## 练习: Level 1

1. 什么是组件生命周期
2. 生命周期的目的是什么
3. 组件生命周期的三个阶段是什么
4. mounting是什么意思?
5. updating是什么意思？
6. unmounting是什么意思？
7. 最常见的内置安装生命周期方法是什么?
8. mounting生命周期方法有哪些?
9. updating生命周期方法有哪些?
10. unmounting生命周期方法有哪些?

## 练习: Level 2

敬请期待

## 练习: Level 3

敬请期待

🎉 CONGRATULATIONS ! 🎉

[<< 第十三天](../13_Day_Controlled_Versus_Uncontrolled_Input/13_uncontrolled_input-CN.md) | [第十五天 >>](../15_Third_Party_Packages/15_third_party_packages-CN.md)
