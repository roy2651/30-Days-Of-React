<div align="center">
  <h1> 30 Days Of React: React项目文件夹结构</h1>
</div>

[<< 第九天](../09_Day_Conditional_Rendering/09_conditional_rendering-CN.md) | [第十一天 >>](../11_Day_Events/11_events-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_10.jpg)

- [React项目文件夹结构和文件命名](#react项目文件夹结构和文件命名)
  - [文件命名](#文件命名)
  - [文件夹](#文件夹)
  - [组件文件夹](#组件文件夹)
  - [Fragments](#fragments)
- [练习题](#练习题)
  - [练习:Level 1](#练习level-1)
  - [练习:Level 2](#练习level-2)
  - [练习: Level 3](#练习-level-3)

# React项目文件夹结构和文件命名

在React项目中，没有严格的方法使用单个文件夹结构或文件命名。大多数情况下，团队可以做出这些选择。有时，一家公司可能已制定了有关遵循哪些代码约定，文件夹结构和文件命名的指南。构造React项目没有正确或错误的方法，但是某些结构在可伸缩性，可维护性，易于处理文件和易于理解的结构方面优于其他结构。如果您想进一步了解文件夹结构，可以查看以下文章。

- [React Folder Structure by https://www.devaradise.com ](https://www.devaradise.com/react-project-folder-structure)
- [React Folder Structure by www.robinwieruch.de ](https://www.robinwieruch.de/react-folder-structure)
- [React Folder Structure by Faraz Ahmad](https://dev.to/farazamiruddin/an-opinionated-guide-to-react-folder-structure-file-naming-1l7i)
- [React Folder Structure by https://maxrozen.com/](https://maxrozen.com/guidelines-improve-react-app-folder-structure/)

我混合使用了不同的约定。如果您愿意，可以遵循它，但是请坚持使用您认为对您有意义的结构。

## 文件命名

在我所有的React项目中，我将对所有组件使用驼峰式文件名。我更喜欢使用描述性的长名

## 文件夹

我发现将所有图像，图标和字体轻松地放入静态资源文件夹，并将所有CSS样式表都放入样式文件夹很容易。所有组件都将在components文件夹中。

到目前为止，我们一直在研究index.js文件。我们在index.js上有很多组件。今天，我们将每个组件移至单个文件，并将所有文件导入App.js。在此过程中，您将看到我的文件夹结构。当前，我们在src目录中。所有文件夹结构都将在src目录中。让我们从index.js文件开始。除了index.js文件之外，我们还创建一个App.js文件并将当前必须使用的大多数组件移至App.js。使用index.js可以轻松地将组件与index.html连接。

```js
// src/index.js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

const App = () => <h1>Welcome to 30 Days Of React</h1>

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

在上面的代码片段中，我们有App组件。让我们将App组件创建到其自己的文件App.js

```js
// src/App.js
import React from 'react
const App = () => <h1>Welcome to 30 Days Of React</h1>
```

我们必须导出组件才能将其导入另一个文件。我们可以将其导出为默认导出或命名导出。在一个文件中，我们可以进行一个默认导出和多个命名导出。首先，让我们使用名称导出来实现它，然后再使用默认导出。

我们只在 _let_ 或 _const_ 之前添加关键字 _export_ 即可进行命名导出。

```js
// src/App.js
import React from 'react

// named export in arrow function
export const App = () => <h1>Welcome to 30 Days Of React</h1>
```

在函数声明中导出常规函数

```js
// src/App.js
import React from 'react
// named export in regular function, function declaration
export function App () {
return <h1>Welcome to 30 Days Of React</h1>
}
```

现在，让我们将App组件从App.js文件导入index.js。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import { App } from './App'

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

我们看到了一个命名的导出，现在让我们使用默认导出来实现它。我们可以通过两种方式做到这一点，但是如果要导出组件，建议使用第二种方式，因为有时我们可能会将一个组件与另一个更高阶的组件绑定在一起。

```js
// src/App.js
import React from 'react
// export default in arrow function
export default const App = () => <h1>Welcome to 30 Days Of React</h1>

```

```js
// src/App.js
import React from 'react
// export default in arrow function
export default function App () {
  return <h1>Welcome to 30 Days Of React</h1>
}
```

```js
// src/App.js
// Recommended for most of the cases
import React from 'react
const App = () => <h1>Welcome to 30 Days Of React</h1>
export default App
```

如果将组件默认导出，则在导入期间不需要大括号。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如果您还记得的话，到目前为止，我们已经创建了以下组件，并且已经将它们组合在一起。这样的工作并不容易。现在，我们将它们所有组件移动到单独的文件中。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images'
import { countriesData } from './data/countries'

// Header component
class Header extends React.Component {
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

const Country = ({
  country: { name, capital, flag, languages, population, currency },
}) => {
  const formatedCapital =
    capital.length > 0 ? (
      <>
        <span>Capital: </span>
        {capital}
      </>
    ) : (
      ''
    )
  const formatLanguage = languages.length > 1 ? `Languages` : `Language`
  return (
    <div className='country'>
      <div className='country_flag'>
        <img src={flag} alt={name} />
      </div>
      <h3 className='country_name'>{name.toUpperCase()}</h3>
      <div class='country_text'>
        <p>{formatedCapital}</p>
        <p>
          <span>{formatLanguage}: </span>
          {languages.join(', ')}
        </p>
        <p>
          <span>Population: </span>
          {population.toLocaleString()}
        </p>
        <p>
          <span>Currency: </span>
          {currency}
        </p>
      </div>
    </div>
  )
}

// User Card Component
const UserCard = () => (
  <div className='user-card'>
    <img src={asabenehImage} alt='asabeneh image' />
    <h2>Asabeneh Yetayeh</h2>
  </div>
)

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

const Message = ({ message }) => (
  <div>
    <h1>{message}</h1>
  </div>
)
const Login = () => (
  <div>
    <h3>Please Login</h3>
  </div>
)
const Welcome = (props) => (
  <div>
    <h1>Welcome to 30 Days Of React</h1>
  </div>
)

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// TechList Component
// class base component
class TechList extends React.Component {
  render() {
    const { techs } = this.props
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Class Component
class Main extends React.Component {
  render() {
    const {
      techs,
      greetPeople,
      handleTime,
      loggedIn,
      handleLogin,
      message,
    } = this.props
    console.log(message)

    const status = loggedIn ? <Welcome /> : <Login />
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList techs={this.props.techs} />
          </ul>
          {techs.length === 3 && (
            <p>You have all the prerequisite courses to get started React</p>
          )}
          <div>
            <Button
              text='Show Time'
              onClick={handleTime}
              style={buttonStyles}
            />{' '}
            <Button
              text='Greet People'
              onClick={greetPeople}
              style={buttonStyles}
            />
            {!loggedIn && <p>Please login to access more information about 30 Days Of React challenge</p>}
          </div>
          <div style={{ margin: 30 }}>
            <Button
              text={loggedIn ? 'Logout' : 'Login'}
              style={buttonStyles}
              onClick={handleLogin}
            />
            <br />
            {status}
          </div>
          <Message message={message} />
        </div>
      </main>
    )
  }
}

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: 3,
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
  margin: '0 auto',
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
  state = {
    loggedIn: false,
    techs: ['HTML', 'CSS', 'JS'],
    message: 'Click show time or Greet people to change me',
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
  }
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
    return `${month} ${date}, ${year}`
  }
  handleTime = () => {
    let message = this.showDate(new Date())
    this.setState({ message })
  }
  greetPeople = () => {
    let message = 'Welcome to 30 Days Of React Challenge, 2020'
    this.setState({ message })
  }

  render() {
    const data = {
      welcome: '30 Days Of React',
      title: 'Getting Started React',
      subtitle: 'JavaScript Library',
      author: {
        firstName: 'Asabeneh',
        lastName: 'Yetayeh',
      },
      date: 'Oct 9, 2020',
    }
    const techs = ['HTML', 'CSS', 'JavaScript']

    return (
      <div className='app'>
        {this.state.backgroundColor}
        <Header data={data} />

        <Main
          techs={techs}
          handleTime={this.handleTime}
          greetPeople={this.greetPeople}
          loggedIn={this.state.loggedIn}
          handleLogin={this.handleLogin}
          message={this.state.message}
        />

        <Footer date={new Date()} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

## 组件文件夹

在src目录中，将拉出所有组件

```sh
src
  App.js
  index.js
  components
   -auth
    -Signup.js
    -Signin.js
    -Forgotpassword.js
    -Resetpassord.js
  header
   -Header.js
  footer
   -Footer.js
  assets
   -images
   -icnons
   - fonts
  styles
   -button.js
   -button.scss
 utils
  -random-id.js
  -display-time.js
  -generate-color.js
 shared
  -Button.js
  -InputField.js
  -TextAreaField.js
```

让我们在src内创建components目录，并在组件内创建header目录。在header目录中创建Header.js。

```js
// src/components/header/Header.js
import React from 'react'

const Header = (props) => {
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

export default Header
```

与页眉类似，让我们将所有组件移动到它们各自的文件中。index.html上的所有CSS文件都将移入样式文件夹，然后将每个部分拆分成各自的文件，然后尝试检查样式文件夹

## Fragments

Fragments 是避免JSX中不必要的父元素的一种方法。让我们实现一个片段。我们从react模块导入片段。如下所示，我们使用逗号分隔将React和fragment一起导入

```js
import React, { Fragment } from 'react'

const Skills = () => {
  return (
    <Fragment>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </Fragment>
  )
}
const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```

如下所示，也可以从React中提取片段模块。

```js
import React from 'react'

const Skills = () => {
  return (
    <React.Fragment>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </React.Fragment>
  )
}

const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```

在最新版本的Reacts中，也可以使用此符号进行提取而无需提取或导入（<> </>）

```js
import React from 'react'

// Recommended
const Skills = () => {
  return (
    <>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </>
  )
}

const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```

当我们制作一个基于类的组件时，我们一直在使用React.Component，而我们只需要导入该组件，代码就会看起来更加干净。让我们来看一个例子。

```js
import React from 'react'

// without importing the Component
// Not recommended
class App extends React.Component {
  render() {
    return <h1> 30 Days of React </h1>
  }
}
```

```js
import React, { Component } from 'react'

// This is recommended
class App extends Component {
  render() {
    return <h1> 30 Days of React </h1>
  }
}
```

做得好。是时候为您的大脑和肌肉做一些运动了

# 练习题

## 练习:Level 1

1. What is the importance of React Folder Structure and File Naming
2. How do you export file
3. How do you  import file
4. Make a component of module and export it as named or default export
5. Make a component or module and import it
6. Change all the components you have to different folder structure

## 练习:Level 2

1. Make a simple portfolio using the components we have created so far. Implement a dark mode by using the function we wrote on day 8 challenge.

## 练习: Level 3

待续...

🎉 CONGRATULATIONS ! 🎉

[<< 第九天](../09_Day_Conditional_Rendering/09_conditional_rendering-CN.md) | [第十一天 >>](../11_Day_Events/11_events-CN.md)
