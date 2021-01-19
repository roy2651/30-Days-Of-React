<div align="center">
  <h1> 30 Days Of React: 类组件 </h1>

</div>

[<< 第六天](../06_Day_Map_List_Keys/06_map_list_keys-CN.md) | [第八天 >>](../08_Day_States/08_states-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_7.jpg)

- [类组件](#类组件)
  - [在类组件中访问Props](#在类组件中访问props)
  - [基于类的组件中的方法](#基于类的组件中的方法)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 类组件

在前面的部分章节中，我们介绍了JSX，功能组件和Props。在本节中，我们将介绍类组件或有状态组件。仅基于类的组件曾经具有状态和生命周期方法。但是，在React版本16.8.0之后，使用React Hooks可以使功能组件具有状态和生命周期。在30天的React挑战中，我们将介绍16.8.0之前和之后的React，这意味着旧版本和最新版本。有许多用较旧版本编写的代码，有时可能需要迁移。另外，要很好地理解React，还必须了解基于类的组件。

之前所有的组件都是功能组件。让我们也制作基于类的组件。基于类的组件是使用JavaScript类制作的，它继承自react Component。让我们学习如何通过转换之前制作的所有功能组件来制作基于类的组件。转换所有内容并不重要，但是为了学习如何将功能组件更改为类组件，我们正在转换它们。

```js
// Pure JavaScript class and child
// Imagine this what we import from React package
class Component {
  constructor(props) {}
}

// This how we make class based components by inheriting from the parent
class Child extends Component {
  constructor(props) {
    super(props)
  }
}
```

函数式React组件

```js
// index.js

import React from 'react'
import ReactDOM from 'react-dom'
// Header Component
// Functional component
const Header = () => (
  <header>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 6, 2020</small>
    </div>
  </header>
)
const rootElement = document.getElementById('root')
ReactDOM.render(<Header />, rootElement)
```

基于类的React组件是React.Component的子级，它具有内置的render方法，并且可能具有构造函数。

```js
//index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  render() {
    return (
      <header>
        <div className='header-wrapper'>
          <h1>Welcome to 30 Days Of React</h1>
          <h2>Getting Started React</h2>
          <h3>JavaScript Library</h3>
          <p>Asabeneh Yetayeh</p>
          <small>Oct 7, 2020</small>
        </div>
      </header>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<Header />, rootElement)
```

让我们看一下上面带有构造函数的组件

```js
//index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class base component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    return (
      <header>
        <div className='header-wrapper'>
          <h1>Welcome to 30 Days Of React</h1>
          <h2>Getting Started React</h2>
          <h3>JavaScript Library</h3>
          <p>Asabeneh Yetayeh</p>
          <small>Oct 7, 2020</small>
        </div>
      </header>
    )
  }
}
const rootElement = document.getElementById('root')
ReactDOM.render(<Header />, rootElement)
```

让我们将所有功能组件更改为基于类的组件

```js
// TechList Component
// functional component
const TechList = () => {
  const techs = ['HTML', 'CSS', 'JavaScript']
  const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
  return techsFormatted
}

// TechList Component
// class base component
class TechList extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    const techs = ['HTML', 'CSS', 'JavaScript']
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Functional Component
const Main = () => (
  <main>
    <div className='main-wrapper'>
      <p>Prerequisite to get started react.js:</p>
      <ul>
        <TechList />
      </ul>
    </div>
  </main>
)

// Main Component
// Class Component
class Main extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList />
          </ul>
        </div>
      </main>
    )
  }
}

// Footer Component
// Functional component
const Footer = () => (
  <footer>
    <div className='footer-wrapper'>
      <p>Copyright 2020</p>
    </div>
  </footer>
)

// Footer Component
// Class component
class Footer extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <footer>
        <div className='footer-wrapper'>
          <p>Copyright 2020</p>
        </div>
      </footer>
    )
  }
}

// The App, or the parent or the container component
// Functional Component
const App = () => (
  <div className='app'>
    <Header />
    <Main />
    <Footer />
  </div>
)

// The App, or the parent or the container component
// Class Component
class App extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <div className='app'>
        <Header />
        <Main />
        <Footer />
      </div>
    )
  }
}
```

让我们将所有基于类的组件放到一个文件中。

```js
//index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class base component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    return (
      <header>
        <div className='header-wrapper'>
          <h1>Welcome to 30 Days Of React</h1>
          <h2>Getting Started React</h2>
          <h3>JavaScript Library</h3>
          <p>Asabeneh Yetayeh</p>
          <small>Oct 7, 2020</small>
        </div>
      </header>
    )
  }
}

// TechList Component
// class base component
class TechList extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    const techs = ['HTML', 'CSS', 'JavaScript']
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Class Component
class Main extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList />
          </ul>
        </div>
      </main>
    )
  }
}

// Footer Component
// Class component
class Footer extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <footer>
        <div className='footer-wrapper'>
          <p>Copyright 2020</p>
        </div>
      </footer>
    )
  }
}

// The App, or the parent or the container component
// Class Component
class App extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <div className='app'>
        <Header />
        <Main />
        <Footer />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 在类组件中访问Props

我们说过，props是一种将数据从组件上发送到另一个组件的方法，或者我们可以说props是数据载体。因此，我们也应该在基于类的组件中处理props。我们可以使用关键字 _this_ 来访问基于类的组件的props 。请参见下面的示例。

```js
// index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    return (
      <header>
        <div className='header-wrapper'>
          <h1>{this.props.data.welcome}</h1>
          <h2>{this.props.data.title}</h2>
          <h3>
            {this.props.data.author.firstName} {this.props.data.author.lastName}
          </h3>
          <small>{this.props.data.date}</small>
        </div>
      </header>
    )
  }
}
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: 'Oct 7, 2020',
  }

  return (
    <div className='app'>
      <Header data={data} />
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如您在上面的示例中看到的那样，为了从props中获取数据，我们每次都编写 _props.data_ 。我们可以使用解构来避免这种重复。


```js
// index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    console.log(this.props.data)
    const {
      welcome,
      title,
      subtitle,
      author: { firstName, lastName },
      date,
    } = this.props.data

    return (
      <header>
        <div className='header-wrapper'>
          <h1>{welcome}</h1>
          <h2>{title}</h2>
          <h3>{subtitle}</h3>
          <p>
            {firstName} {lastName}
          </p>
          <small>{date}</small>
        </div>
      </header>
    )
  }
}
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: 'Oct 6, 2020',
  }

  return (
    <div className='app'>
      <Header data={data} />
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如您所见，上面的代码比以前的代码更干净。现在，让我们清洁所有的组件并将它们放在一起。

```js
// index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    console.log(this.props.data)
    const {
      welcome,
      title,
      subtitle,
      author: { firstName, lastName },
      date,
    } = this.props.data

    return (
      <header>
        <div className='header-wrapper'>
          <h1>{welcome}</h1>
          <h2>{title}</h2>
          <h3>{subtitle}</h3>
          <p>
            {firstName} {lastName}
          </p>
          <small>{date}</small>
        </div>
      </header>
    )
  }
}

// TechList Component
// class base component
class TechList extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    const { techs } = this.props
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Class Component
class Main extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList techs={this.props.techs} />
          </ul>
        </div>
      </main>
    )
  }
}

// Footer Component
// Class component
class Footer extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <footer>
        <div className='footer-wrapper'>
          <p>Copyright {this.props.date.getFullYear()}</p>
        </div>
      </footer>
    )
  }
}

class App extends React.Component {
  render() {
    const data = {
      welcome: 'Welcome to 30 Days Of React',
      title: 'Getting Started React',
      subtitle: 'JavaScript Library',
      author: {
        firstName: 'Asabeneh',
        lastName: 'Yetayeh',
      },
      date: 'Oct 7, 2020',
    }
    const techs = ['HTML', 'CSS', 'JavaScript']

    return (
      <div className='app'>
        <Header data={data} />
        <Main techs={techs} />
        <Footer date={new Date()} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 基于类的组件中的方法

我们访问基于类的组件中的方法。大多数时候，我们在父组件上编写不同的方法，然后将它们传递给子组件。让我们看一下实现。

让我们在此组件上添加一个方法

```js
//index.js

import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge, 2020')
  }
  render() {
    return (
      <header>
        <div className='header-wrapper'>
          <h1>Welcome to 30 Days Of React</h1>
          <h2>Getting Started React</h2>
          <h3>JavaScript Library</h3>
          <p>Asabeneh Yetayeh</p>
          <small>Oct 7, 2020</small>
          <button onClick={this.greetPeople}> Greet </button>
        </div>
      </header>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<Header />, rootElement)
```

事件发生时触发方法的调用或调用。因此，无论何时将方法传递给事件侦听器，都不要调用该方法。

现在，让我们添加所有必需的方法的代码。

```js
// index.js

import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images/asabeneh.jpg'

// Fuction to show month date year

// User Card Component
const UserCard = ({ user: { firstName, lastName, image } }) => (
  <div className='user-card'>
    <img src={image} alt={firstName} />
    <h2>
      {firstName}
      {lastName}
    </h2>
  </div>
)

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: 3,
  cursor: 'pointer',
  fontSize: 18,
  color: 'white',
}

// class based component
class Header extends React.Component {
  constructor(props) {
    super(props)
    // the code inside the constructor run before any other code
  }
  render() {
    console.log(this.props.data)
    const {
      welcome,
      title,
      subtitle,
      author: { firstName, lastName },
      date,
    } = this.props.data

    return (
      <header>
        <div className='header-wrapper'>
          <h1>{welcome}</h1>
          <h2>{title}</h2>
          <h3>{subtitle}</h3>
          <p>
            {firstName} {lastName}
          </p>
          <small>{date}</small>
        </div>
      </header>
    )
  }
}

// TechList Component
// class base component
class TechList extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    const { techs } = this.props
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Class Component
class Main extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList techs={this.props.techs} />
          </ul>
          <UserCard user={this.props.user} />
          <Button
            text='Greet People'
            onClick={this.props.greetPeople}
            style={buttonStyles}
          />
          <Button
            text='Show Time'
            onClick={this.props.handleTime}
            style={buttonStyles}
          />
        </div>
      </main>
    )
  }
}

// Footer Component
// Class component
class Footer extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <footer>
        <div className='footer-wrapper'>
          <p>Copyright {this.props.date.getFullYear()}</p>
        </div>
      </footer>
    )
  }
}

class App extends React.Component {
  showDate = (time) => {
    const months = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December',
    ]

    const month = months[time.getMonth()].slice(0, 3)
    const year = time.getFullYear()
    const date = time.getDate()
    return ` ${month} ${date}, ${year}`
  }
  handleTime = () => {
    alert(this.showDate(new Date()))
  }
  greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge, 2020')
  }
  render() {
    const data = {
      welcome: 'Welcome to 30 Days Of React',
      title: 'Getting Started React',
      subtitle: 'JavaScript Library',
      author: {
        firstName: 'Asabeneh',
        lastName: 'Yetayeh',
      },
      date: 'Oct 7, 2020',
    }
    const techs = ['HTML', 'CSS', 'JavaScript']

    // copying the author from data object to user variable using spread operator
    const user = { ...data.author, image: asabenehImage }

    return (
      <div className='app'>
        <Header data={data} />
        <Main
          user={user}
          techs={techs}
          handleTime={this.handleTime}
          greetPeople={this.greetPeople}
        />

        <Footer date={new Date()} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

大多数情况下，容器或父组件可以被编写为类组件，而其他组件可以被编写为功能或表示组件。数据通常从父组件流到子组件，并且是单向的。但是，最新版本的react可以使我们仅使用函数式组件来编写应用程序中的每个组件。在以前的版本中这是不可能的。在下一节中，我们将介绍状态，这是React的核心。状态允许每当状态发生变化时重新渲染React组件。

# 练习题

## 练习: Level 1

1. 您如何编写纯JavaScript函数
2. 什么是继承？ 如何从父到子传递?
3. 什么是基于类的React组件 ?
4. 函数式React组件和基于类的React组件有什么区别 ?
5. 什么时候需要使用基于类的组件而不是函数组件
6. 基于类的组件的用例是什么 ?
7. 哪种类型的组件最常使用？功能或基于类的组件
8. 什么是React生命周期 ? (尚未开始) 
9. React中的状态是什么 ? (尚未开始)

## 练习: Level 2

通过将以前的练习改为基于类的组件，了解有关基于类的组件的更多信息

## 练习: Level 3

即将来临 ...

🎉 CONGRATULATIONS ! 🎉

[<< 第六天](../06_Day_Map_List_Keys/06_map_list_keys-CN.md) | [第八天 >>](../08_Day_States/08_states-CN.md)
