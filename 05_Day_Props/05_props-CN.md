<div align="center">
  <h1> 30 Days Of React: Props </h1>
</div>

[<< 第四天](../04_Day_Component/04_components-CN.md) | [第六天 >>](../06_Day_Map_List_Keys/06_map_list_keys-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_5.jpg)

- [Props](#props)
  - [功能组件中的Props](#功能组件中的props)
  - [什么是props?](#什么是props)
  - [Props 对象](#props-对象)
    - [不同的数据类型props](#不同的数据类型props)
    - [String props 类型](#string-props-类型)
    - [Number props 类型](#number-props-类型)
    - [布尔 props 类型](#布尔-props-类型)
    - [数组 props 类型](#数组-props-类型)
    - [对象 props 类型](#对象-props-类型)
    - [函数 prop 类型](#函数-prop-类型)
  - [解构 props](#解构-props)
  - [propTypes](#proptypes)
  - [defaultProps](#defaultprops)
- [练习: 组件 和 Props](#练习-组件-和-props)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# Props

## 功能组件中的Props

在前一天，我们看到了如何向React组件JSX注入不同的数据类型。现在，让我们看看如何在组件中使用它，以及如何将不同的数据作为Props传递。

## 什么是props?

Props是React中的一个特殊关键字，代表属性，用于将数据从一个组件传递到另一个组件，主要是从父组件传递到子组件。可以说Props是数据载体或数据传输手段

希望您熟悉JavaScript函数。大多数时候，带有参数的函数很聪明，它们可以获取动态数据，就像props是我们将数据或参数传递给组件的一种方式。让我们看看函数和组件之间的区别。

```js
// function syntax

const getUserInfo = (firstName, lastName, country) => {
  return `${firstName} ${lastName}. Lives in ${country}.`
}

// calling a functons

getUserInfo('Asabeneh', 'Yeteyeh', 'Finland')

//component syntax

// User component, component should start with an uppercase
const User = (props) => {
  return (
    <div>
      <h1>
        {props.firstName}
        {props.lastName}
      </h1>
      <small>{props.country}</small>
    </div>
  )
}
// calling or instantiating a component, this component has three properties and we call them props:firstName, lastName, country
<User firstName = 'Asabeneh', lastName='Yetayeh' country = 'Finland' />
```

在上一节中，我们按如下方式注入了数据，今天我们将这些数据更改为props。

```js
const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const author = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
}
const date = 'Oct 4, 2020'

// Header Component
const Header = () => (
  <header>
    <div className='header-wrapper'>
      <h1>{welcome}</h1>
      <h2>{title}</h2>
      <h3>{subtitle}</h3>
      <p>
        {author.firstName} {author.lastName}
      </p>
      <small>{date}</small>
    </div>
  </header>
)
```

除了注入数据，我们还可以将数据作为props传递。React Props类似于函数中的参数。

## Props 对象

React props是创建React组件时立即获得的对象。在将属性传递给组件之前，让我们检查一下在props对象中得到什么。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = (props) => {
  console.log(props) // empty object, {}
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {author.firstName} {author.lastName}
        </p>
        <small>{date}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  return (
    <div className='app'>
      <Header />
    </div>
  )
}

const rootElement = document.getElementById('root')

ReactDOM.render(<App />, rootElement)
```

在上面的console.log（props）中，您将获得一个空对象 {}。这意味着，如果在实例化组件时未传递任何属性或属性，则props将为空，否则它将使用您作为属性传递的数据填充，并且这些属性的正确名称是props。

让我们从一个简单的例子开始。在下面的示例中，欢迎字符串已作为props传递到Header组件中。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = (props) => {
  console.log(props) // {welcome:'Welcome to 30 Days Of React'}
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{props.welcome}</h1>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  return (
    <div className='app'>
      <Header welcome='Welcome to 30 Days Of React' />
    </div>
  )
}

const rootElement = document.getElementById('root')

ReactDOM.render(<App />, rootElement)
```

现在，当您执行console.log（props）时，您应该获得以下对象，这意味着我们可以在props对象内找到传递给Header组件的welcome属性。

```js
{
  welcome: 'Welcome to 30 Days Of React'
}
```

如您在上面的代码中看到的，我们仅将单个props传递给Header组件，即welcome props。一个组件可以具有一个或多个props。props可能是不同的数据类型。它可以是字符串，数字，布尔值，数组，对象或函数。在下一节中，我们将介绍各种props。

### 不同的数据类型props

### String props 类型

我们将属性传递给组件的props的数据类型是字符串。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = (props) => {
  console.log(props)
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{props.welcome}</h1>
        <h2>{props.title}</h2>
        <h3>{props.subtitle}</h3>
        <p>
          {props.firstName} {props.lastName}
        </p>
        <small>{props.date}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => (
  <div className='app'>
    <Header
      welcome='Welcome to 30 Days Of React'
      title='Getting Started React'
      subtitle='JavaScript Library'
      firstName='Asabeneh'
      lastName='Yetayeh'
      date='Oct 4, 2020'
    />
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如果在浏览器控制台上检查，将得到以下对象。

```js
{
firstName: "Asabeneh",
lastName: "Yetayeh",
date: "Oct 4, 2020"
subtitle: "JavaScript Library"
title: "Getting Started React"
welcome: "Welcome to 30 Days Of React"
}
```

由于您现在是JavaScript专业，因此您知道该对象的用途。

从上面的示例可以看到，道具的值是静态写入的。但是，如果要应用某些逻辑，则很难用静态写入的数据来实现，因此最好使用变量作为道具。让我们看下面的例子：

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = (props) => (
  <header>
    <div className='header-wrapper'>
      <h1>{props.welcome}</h1>
      <h2>{props.title}</h2>
      <h3>{props.subtitle}</h3>
      <p>
        {props.firstName} {props.lastName}
      </p>
      <small>{props.date}</small>
    </div>
  </header>
)

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const welcome = 'Welcome to 30 Days Of React'
  const title = 'Getting Started React'
  const subtitle = 'JavaScript Library'
  const firstName = 'Asabeneh'
  const lastName = 'Yetayeh'
  const date = 'Oct 4, 2020'

  return (
    <div className='app'>
      <Header
        welcome={welcome}
        title={title}
        subtitle={subtitle}
        firstName={firstName}
        lastName={lastName}
        date={date}
      />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### Number props 类型

让我们对组件使用数字props

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Age = (props) => <div>The person is {props.age} years old.</div>
const Weight = (props) => (
  <p>The weight of the object on earth is {props.weight} N.</p>
)

// The App, or the parent or the container component
// Functional Component
const App = () => {
  let currentYear = 2020
  let birthYear = 1820
  const age = currentYear - birthYear
  const gravity = 9.81
  const mass = 75

  return (
    <div className='app'>
      <Age age={age} />
      <Weight weight={gravity * mass} />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### 布尔 props 类型

我们可以将布尔数据类型传递给React组件。

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Status = (props) => {
  // ternary operator to check the status of the person
  let status = props.status ? 'Old enough to drive' : 'Too young for driving'
  return <p>{status}</p>
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  let currentYear = 2020
  let birthYear = 2015
  const age = currentYear - birthYear // 15 years

  let status = age >= 18

  return (
    <div className='app'>
      <Status status={status} />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### 数组 props 类型

在编程中，数组和对象是最常用的数据结构，用于解决不同的问题并以结构化的方式存储数据。因此，我们经常遇到数组形式的数据。让我们将数组作为props传递给组件

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Skills = (props) => <ul>{props.skills}</ul>

const App = () => (
  <div className='app'>
    <Skills skills={['HTML', 'CSS', 'JavaScript']} />
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如果您在浏览器上看到结果，则技能元素需要格式化。因此，在渲染之前，每个技能之间应该具有一些要素。要修改数组并添加li元素，我们可以使用map方法。您应该非常熟悉函数式编程映射，过滤和归类，否则，请熟悉第1天JavaScript复习。让我们应用map来修改数组。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Skills Component
const Skills = (props) => {
  // modifying the skills array
  const skillList = props.skills.map((skill) => <li>{skill}</li>)
  return <ul>{skillList}</ul>
}

const App = () => (
  <div className='app'>
    <Skills skills={['HTML', 'CSS', 'JavaScript']} />
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

我们将在其他部分中深入介绍列表和地图。现在，让我们将对象视为props。

### 对象 props 类型

我们可以将对象作为props传递给React组件。让我们来看一个例子。我们可以将以前的Header props更改为对象。目前，让我们更改一些属性以更好地理解。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = (props) => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{props.data.welcome}</h1>
        <h2>{props.data.title}</h2>
        <h3>{props.data.subtitle}</h3>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
  }

  return (
    <div className='app'>
      <Header data={data} />
    </div>
  )
}
const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

现在，让我们将所有以前的Header属性更改为一个对象。

```js
import React from 'react'
import ReactDOM from 'react-dom'

const showDate = (time) => {
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
// Header Component
const Header = (props) => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{props.data.welcome}</h1>
        <h2>{props.data.title}</h2>
        <h3>{props.data.subtitle}</h3>
        <p>
          {props.data.author.firstName} {props.data.author.lastName}
        </p>
        <small>{showDate(props.data.date)}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: new Date(), // date needs to be formatted to a human readable format
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

当我们使用对象作为props时，我们通常会对数据进行解构以访问值。分解使我们的代码易于阅读。我们很快就会看到props的破坏，但在此之前，让我们将功能视为React组件的props。

### 函数 prop 类型

我们可以将一个函数作为props类型传递给React组件。让我们看一些例子

```js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component

const Button = (props) => <button onClick={props.onClick}>{props.text}</button>

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const sayHi = () => {
    alert('Hi')
  }

  return (
    <div className='app'>
      <Button text='Say Hi' onClick={sayHi} />
    </div>
  )
}
const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

甚至我们可以在大括号内编写一个函数

```js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component

const Button = (props) => <button onClick={props.onClick}>{props.text}</button>

// The App, or the parent or the container component
// Functional Component
const App = () => {
  return (
    <div className='app'>
      <Button text='Say Hi' onClick={() => alert('Hi')} />
    </div>
  )
}
const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

现在，让我们实现不同的函数作为props

```js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component

const Button = (props) => <button onClick={props.onClick}>{props.text}</button>

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge, 2020')
  }

  return (
    <div className='app'>
      <Button text='Greet People' onClick={greetPeople} />
      <Button text='Show Time' onClick={() => alert(new Date())} />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

在上面的示例中，onClick是持有greetPeople函数的props。HTML具有onclick，onmouseover，onhover，onkeypress等事件处理程序。在React中，这些处理程序位于camelCase中。例如onClick，onMouseOver，onKeyPress等。我们将在其他部分中详细介绍React中的事件。

让我们看一些更多的作为props的函数，以清楚地了解如何在React组件中处理作为props的函数。

此组件将月份，日期和年份显示为警报框。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Function to display time in Mon date, year format eg Oct 4, 2020
const showDate = (time) => {
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

// A button component

const Button = (props) => <button onClick={props.onClick}>{props.text}</button>

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const handleTime = () => {
    alert(showDate(new Date()))
  }
  const greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge, 2020')
  }
  return (
    <div className='app'>
      <Button text='show time' onClick={handleTime} />
      <Button text='Greet People' onClick={greetPeople} />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 解构 props

到现在为止，我相信您是一名JavaScript专业忍者，并且了解解构数组和对象的知识。对代码进行某种程度的分解使其易于阅读。让我们在Header组件中解构props。我们作为props传递的所有内容都存储在道具对象中。因此，props是一个对象，我们可以破坏属性。让我们分解一下我们在对象props示例中编写的一些props。我们可以通过多种方式进行解构：

1. 逐步解构

```js
import React from 'react'
import ReactDOM from 'react-dom'

const showDate = (time) => {
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
// Header Component
const Header = (props) => {
  const data = props.data
  const { welcome, title, subtitle, author, date } = data
  const { firstName, lastName } = author
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {firstName} {lastName}
        </p>
        <small>{showDate(date)}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: new Date(),
  }

  return (
    <div className='app'>
      <Header data={data} />
    </div>
  )
}
const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

2. 一条线解构

```js
import React from 'react'
import ReactDOM from 'react-dom'

const showDate = (time) => {
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
// Header Component
const Header = (props) => {
  const data = props.data
  const {
    welcome,
    title,
    subtitle,
    author: { firstName, lastName },
    date,
  } = data

  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {firstName} {lastName}
        </p>
        <small>{showDate(date)}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: new Date(),
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

3. 解构括号内的props

```js
import React from 'react'
import ReactDOM from 'react-dom'

const showDate = (time) => {
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
// Header Component
const Header = ({
  data: {
    welcome,
    title,
    subtitle,
    author: { firstName, lastName },
    date,
  },
}) => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {firstName} {lastName}
        </p>
        <small>{showDate(date)}</small>
      </div>
    </header>
  )
}

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: new Date(),
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

现在，让我们分解所有的组件并将它们组装在一起。我们将props从一个组件传递到另一个组件，通常将其从父组件传递到子组件。例如，在Main组件技术中，用户，greetPeople和handleTime props已从父组件Main传递给子组件TechList和UserCard。在下面，您将解构并清理所有代码。

```js
import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images/asabeneh.jpg'

// Fuction to show month date year

const showDate = (time) => {
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

// Header Component
const Header = ({
  data: {
    welcome,
    title,
    subtitle,
    author: { firstName, lastName },
    date,
  },
}) => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {firstName} {lastName}
        </p>
        <small>{showDate(date)}</small>
      </div>
    </header>
  )
}

// TechList Component
const TechList = ({ techs }) => {
  const techList = techs.map((tech) => <li key={tech}>{tech}</li>)
  return techList
}

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

// Main Component
const Main = ({ user, techs, greetPeople, handleTime }) => (
  <main>
    <div className='main-wrapper'>
      <p>Prerequisite to get started react.js:</p>
      <ul>
        <TechList techs={techs} />
      </ul>
      <UserCard user={user} />
      <Button text='Greet People' onClick={greetPeople} style={buttonStyles} />
      <Button text='Show Time' onClick={handleTime} style={buttonStyles} />
    </div>
  </main>
)

// Footer Component
const Footer = ({ copyRight }) => (
  <footer>
    <div className='footer-wrapper'>
      <p>Copyright {copyRight.getFullYear()}</p>
    </div>
  </footer>
)

// The App, or the parent or the container component
// Functional Component
const App = () => {
  const data = {
    welcome: 'Welcome to 30 Days Of React',
    title: 'Getting Started React',
    subtitle: 'JavaScript Library',
    author: {
      firstName: 'Asabeneh',
      lastName: 'Yetayeh',
    },
    date: new Date(), // date needs to be formatted to a human readable format
  }
  const date = new Date()
  const techs = ['HTML', 'CSS', 'JavaScript']
  // copying the author from data object to user variable using spread operator
  const user = { ...data.author, image: asabenehImage }

  const handleTime = () => {
    alert(showDate(new Date()))
  }
  const greetPeople = () => {
    alert('Welcome to 30 Days Of React Challenge, 2020')
  }

  return (
    <div className='app'>
      <Header data={data} />
      <Main
        user={user}
        techs={techs}
        handleTime={handleTime}
        greetPeople={greetPeople}
      />
      <Footer copyRight={date} />
    </div>
  )
}
const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## propTypes

propTypes包可帮助我们分配传递给组件的props的数据类型

## defaultProps

当我们想要某个组件的一些默认props类型时，可以使用defaultProps。

我们将在其他部分中详细介绍propTypes。

# 练习: 组件 和 Props

## 练习: Level 1

1. 什么是React组件中的props？
2. 您如何在React组件中访问props ?
3. 我们可以将哪些数据类型作为props传递给组件 ?
4. 什么是propTypes?
5. 什么是默认propTypes?

## 练习: Level 2

1. 创建一个功能组件并显示以下图像
   ![Front end](../images/frontend_technologies.png)

2. 使用功能组件创建以下设计

![News Letter](../images/news_letter_design.png)

## 练习: Level 3

1.  在示例中使用给定的十六进制颜色生成器来创建这些随机颜色。如果您不知道如何生成十六进制颜色，则可以使用[dummy data generator](https://www.30daysofreact.com/dummy-data)

![Hexadecimal colors](../images/hexadecimal_color_exercise.png)

2. 用功能组件来设计以下用户卡。

![User Card](../images/user_card_design_jsx.png)

🎉 CONGRATULATIONS ! 🎉

[<< 第四天](../04_Day_Component/04_components-CN.md) | [第六天 >>](../06_Day_Map_List_Keys/06_map_list_keys-CN.md)
