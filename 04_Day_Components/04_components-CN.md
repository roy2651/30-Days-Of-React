<div align="center">
  <h1> 30 Days Of React: 组件 </h1>
</div>

[<< 第三天](../30-Days-Of-React/03_Day_Setting_Up/03_setting_up-CN.md) | [第五天 >>](../05_Day_Props/05_props-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_4.jpg)

- [组件](#组件)
  - [组件概览](#组件概览)
  - [JavaScript函数](#javascript函数)
  - [JavaScript类](#javascript类)
  - [创建React组件](#创建react组件)
    - [功能组件](#功能组件)
    - [渲染组件](#渲染组件)
    - [在React Component中将数据注入JSX](#在react-component中将数据注入jsx)
    - [进一步的功能组件](#进一步的功能组件)
- [练习：组成部分](#练习组成部分)
  - [练习： Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 组件

React组件是一个小的，可重用的代码，它负责应用程序UI的一部分。React应用程序是组件的集合。React可以帮助我们构建可重用的组件。下图显示了不同的组件。所有组件具有不同的边框颜色。在React中，我们将不同的组件组装在一起以创建一个应用程序。我们使用JavaScript函数或类来制作组件。如果使用函数，则组件将是功能组件，但是如果使用类，则组件将是基于类的组件。

组件可以是：

- 功能组件/表示组件/无状态组件/哑组件
- 类组件/容器组件/ Statefull组件/智能组件

上面的组件分类不适用于最新版本的React，但是最好了解以前的定义以及以前的版本是如何工作的。

因此，让我们将所有JSX更改为组件。React中的组件是返回JSX的JavaScript函数或类。组件名称必须以大写字母开头，如果名称是两个单词，则应为CamelCase-带有两个驼峰的骆驼。

## 组件概览

在上一节中，我们达成一致，网站或应用程序由按钮，表单，文本，媒体对象，标题，部分，文章和页脚组成。如果我们有一个价值一百万美元的按钮，那么我们可以一直使用此按钮，而不必在需要按钮时重新创建它。输入字段，表单，页眉或页脚也是如此。这就是组件的力量所在。在下图中，页眉，主要和页脚是组件。在主机内部还有一个用户卡组件和一个文本部分组件。所有不同的颜色代表不同的组件。您看到几种颜色？每种颜色代表一个单独的成分。该图中有五个组件。

![Components](../images/components_example.png)

在进入React组件之前，让我们做一些函数和类刷新器。

## JavaScript函数

JavaScript函数可以是常规函数或箭头函数。这些功能并不完全相同，它们之间略有不同

```js
const getUserInfo = (firstName, lastName, country, title, skills) => {
  return `${firstName} ${lastName},  a ${title} developer based in ${country}. He knows ${skills.join(
    ' '
  )} `
}
// When we call this function we need parameters
const skills = ['HTML', 'CSS', 'JS', 'React']
console.log(
  getUserInfo('Asabeneh', 'Yetayeh', 'Finland', 'FullStack Developer', skills)
)
```

## JavaScript类

类是对象的蓝图。我们实例化一个类来创建不同的对象。另外，我们可以通过继承父级的所有方法和属性来创建子级。

```js
class Parent {
  constructor(firstName, lastName, country, title) {
    // we bind the params with this class object using this keyword
    this.firstName = firstName
    this.lastName = lastName
    this.country = country
    this.title = title
  }
  getPersonInfo() {
    return `${this.firstName} ${this.lastName},  a ${this.title} developer base in ${this.country} `
  }
  parentMethod() {
    // code goes here
  }
}

const p1 = new Parent('Asabeneh', 'Yetayeh', 'Finland', 'FullStack Developer')

class Child extends Parent {
  constructor(firstName, lastName, country, title, skills) {
    super(firstName, lastName, country, title)
    this.skills = skills
    // we bind the child params with the this keyword to this child object
  }
  getSkills() {
    let len = this.skills.length
    return len > 0 ? this.skills.join(' ') : 'No skills found'
  }
  childMethod() {
    // code goes here
  }
}

const skills = ['HTML', 'CSS', 'JS', 'React']

const child = new Child(
  'Asabeneh',
  'Yetayeh',
  'Finland',
  'FullStack Developer',
  skills
)
```

我们只是简要介绍了函数和类。React组件是由JavaScript函数或类组成的，所以现在让我们制作一个React组件。

## 创建React组件

### 功能组件

使用JavaScript函数，我们可以创建功能性的React组件。

```js
// React component syntax
// it can be arrow function, function declaration or function expression
const jsx = <tag> Content </tag>
const ComponentName = () => {
  return jsx
}
```

以下表达式是一个JSX元素。

```js
// JSX element, header
const header = (
  <header style={headerStyles}>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 3, 2020</small>
    </div>
  </header>
)

// React Component
const Header = () => {
  return header
}

// or we can just return the JSX

const Header = () => {
  return (
    <header style={headerStyles}>
      <div className='header-wrapper'>
        <h1>Welcome to 30 Days Of React</h1>
        <h2>Getting Started React</h2>
        <h3>JavaScript Library</h3>
        <p>Asabeneh Yetayeh</p>
        <small>Oct 3, 2020</small>
      </div>
    </header>
  )
}

// Even th above code can be written like this
// Explicitly returning the JSX
const Header = () => (
  <header style={headerStyles}>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 3, 2020</small>
    </div>
  </header>
)
```

### 渲染组件

现在，让我们更改所有必须用于组件的JSX元素。当我们调用JSX元素时，我们使用大括号，而当我们调用组件时，我们执行以下操作。如果传递属性，则在调用组件名称时，将其称为props（<ComponentName propsName = {'data-type'} />）。我们将在另一部分中讨论道具。[Code Pen](https://codepen.io/Asabeneh/full/wvaKKEM)

让我们首先呈现Header组件。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// Header Component
const Header = () => (
  <header>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 3, 2020</small>
    </div>
  </header>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(<Header />, rootElement)
```

现在，让我们创建一个App组件，它将包装Header，Main和Footer。然后，App组件将在DOM上呈现。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images/asabeneh.jpg'

// Header Component
const Header = () => (
  <header>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 3, 2020</small>
    </div>
  </header>
)

// User Card Component
const UserCard = () => (
  <div className='user-card'>
    <img src={asabenehImage} alt='asabeneh image' />
    <h2>Asabeneh Yetayeh</h2>
  </div>
)

// TechList Component
const TechList = () => {
  const techs = ['HTML', 'CSS', 'JavaScript']
  const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
  return techsFormatted
}

// Main Component
const Main = () => (
  <main>
    <div className='main-wrapper'>
      <p>Prerequisite to get started react.js:</p>
      <ul>
        <TechList />
      </ul>
      <UserCard />
    </div>
  </main>
)

// Footer Component
const Footer = () => (
  <footer>
    <div className='footer-wrapper'>
      <p>Copyright 2020</p>
    </div>
  </footer>
)

// The App, or the parent or the container component
const App = () => (
  <div className='app'>
    <Header />
    <Main />
    <Footer />
  </div>
)

const rootElement = document.getElementById('root')
// we render the App component using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

![Rendering Components](../images/rendering_componnets.png)

### 在React Component中将数据注入JSX

到目前为止，我们在JSX元素上使用了静态数据。现在，让我们将不同的数据类型传递为动态数据。动态数据可以是字符串，数字，布尔值，数组或对象。让我们逐步查看每种数据类型。要将数据注入JSX，我们使用{}括号。

在本节中，我们仅注入字符串

```js
import React from 'react'
import ReactDOM from 'react-dom'

const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const firstName = 'Asabeneh'
const lastName = 'Yetayeh'
const date = 'Oct 3, 2020'

// JSX element, header
const header = () => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          Instructor: {firstName} {lastName}
        </p>
        <small>Date: {date}</small>
      </div>
    </header>
  )
}
const rootElement = document.getElementById('root')
// we render the App component using the ReactDOM package
ReactDOM.render(<Header />, rootElement)
```

类似于Header组件，我们可以实现Main和Footer组件

```js
// To get the root element from the HTML document
const rootElement = document.querySelector('.root')
// JSX element, header
const welcome = 'Welcome to 30 Days Of React Challenge'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const author = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
}
const date = 'Oct 2, 2020'

// JSX element, header
const Header = () => (
  <header>
    <div className='header-wrapper'>
      <h1>{welcome}</h1>
      <h2>{title}</h2>
      <h3>{subtitle}</h3>
      <p>
        Instructor: {author.firstName} {author.lastName}
      </p>
      <small>Date: {date}</small>
    </div>
  </header>
)

const numOne = 3
const numTwo = 2

const result = (
  <p>
    {numOne} + {numTwo} = {numOne + numTwo}
  </p>
)

const yearBorn = 1820
const currentYear = 2020
const age = currentYear - yearBorn
const personAge = (
  <p>
    {' '}
    {author.firstName} {author.lastName} is {age} years old
  </p>
)

// User Card Component
const UserCard = () => (
  <div className='user-card'>
    <img src={asabenehImage} alt='asabeneh image' />
    <h2>
      {author.firstName} {author.lastName}
    </h2>
  </div>
)

// JSX element, main
const techs = ['HTML', 'CSS', 'JavaScript']
const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)

// JSX element, main
const Main = () => (
  <main>
    <div className='main-wrapper'>
      <div>
        <p>
          Prerequisite to get started{' '}
          <strong>
            <em>react.js</em>
          </strong>
          :
        </p>
        <ul>{techsFormatted}</ul>
        {result}
        {personAge}
      </div>
      <UserCard />
    </div>
  </main>
)

const copyRight = '2020'

// JSX element, footer
const Footer = () => (
  <footer>
    <div className='footer-wrapper'>
      <p>Copyright &copy;{copyRight}</p>
    </div>
  </footer>
)

// JSX element, app
const app = () => (
  <div className='app'>
    <Header />
    <Main />
    <Footer />
  </div>
)

// we render the App component using the ReactDOM package
ReactDOM.render(<App />, rootElement)
```

### 进一步的功能组件

我们已经将第2天的所有JSX元素都转换为功能组件，到目前为止，您已经非常熟悉组件。让我们创建更多组件。组件的最小尺寸是多少？仅返回单个HTML作为JSX的组件被视为一个小组件。按钮组件或警报框组件，或只是输入字段组件。

```js
const Button = () => <button>action</button>
```

所述 _按钮_ 部件由单个HTML按钮元件。让我们使用JavaScript样式对象设置此按钮的样式。所有CSS属性都应为camelCase，以创建一个JavaScript CSS对象。如果我们将没有单位的数字作为CSS值传递，则将其视为px。请参见下面的示例。

```js
const buttonStyles = {
  padding: '10px 20px',
  background: 'rgb(0, 255, 0',
  border: 'none',
  borderRadius: 5,
}
const Button = () => <button style={buttonStyles}> action </button>
```

Button组件是一个哑组件，因为它没有任何参数，并且我们不能动态更改操作文本。我们需要将道具传递给按钮，以动态更改值。我们将在下一节中看到道具。在结束今天的课程之前，让我们制作另一个功能更强大的组件，该组件显示随机的十六进制数。

```js
import React from 'react'
import ReactDOM from 'react-dom'

// Hexadecimal color generator
const hexaColor = () => {
  let str = '0123456789abcdef'
  let color = ''
  for (let i = 0; i < 6; i++) {
    let index = Math.floor(Math.random() * str.length)
    color += str[index]
  }
  return '#' + color
}

const HexaColor = () => <div>{hexaColor()}</div>

const rootElement = document.getElementById('root')
// we render the App component using the ReactDOM package
ReactDOM.render(<HexaColor />, rootElement)
```

# 练习：组成部分

## 练习： Level 1

1. 常规函数和箭头函数有什么区别？
2. 什么是React组件？
3. 您如何制作React功能组件?
4. 纯JavaScript函数和功能组件之间有什么区别?
5. React组件有多小?
6. 我们可以制作按钮或输入字段组件吗?
7. 制作一个可复用的Button组件.
8. 制作一个可复用的InputField组件.
9. 使用div的一个div父元素和一个p子元素制作一个可复用的警报框组件（警告警报框，成功警报框）.

## 练习: Level 2

1. 创建功能组件并显示以下图像
   ![Front end](../images/frontend_technologies.png)

2. 使用功能组件创建以下设计

![News Letter](../images/news_letter_design.png)

## 练习: Level 3

1.  在示例中使用给定的十六进制颜色生成器创建这些随机颜色

![Hexadecimal colors](../images/hexadecimal_color_exercise.png)

2. 使用功能组件来设计以下用户卡。

   ![User Card](../images/user_card_design_jsx.png)

🎉 CONGRATULATIONS ! 🎉

[<< 第三天](../30-Days-Of-React/03_Day_Setting_Up/03_setting_up.md) | [第五天 >>](../05_Day_Props/05_props.md)
