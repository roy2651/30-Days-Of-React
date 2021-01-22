<div align="center">
  <h1> 30 Days Of React:第三方库</h1>
</div>

[<< 第十四天](../14_Day_Component_Life_Cycles/14_component_life_cycles-CN.md) | [第十六天 >>](../16_Higher_Order_Component/16_higher_order_component-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_15.jpg)

- [第三方库](#第三方库)
  - [NPM or Yarn](#npm-or-yarn)
    - [node-sass](#node-sass)
    - [CSS 模块](#css-模块)
    - [axios](#axios)
    - [react-icons](#react-icons)
    - [moment](#moment)
    - [styled-components](#styled-components)
    - [reactstrap](#reactstrap)
    - [lodash](#lodash)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# 第三方库

npm注册表上有超过140万个JavaScript软件包。到目前为止，几乎每种问题都有一套解决方案。我们不必创建轮子，而必须知道如何使用轮子。在本节中，我们将学习如何使用npm软件包，还将为React应用程序实现最常见的软件包。截至2020年10月10日，npm注册表受欢迎的软件包，软件包总数，每周下载和每月下载似乎如下所示。

![NPM packages](../images/npm_package_day_15.png)

以一种或另一种方式，您很多需要在React应用程序中使用以下软件包。对于某些项目而言，特别重要的是node-sass, moment and axios。

- [node-sass](https://www.npmjs.com/package/node-sass)
- [moment](https://www.npmjs.com/package/moment)
- [axios](https://www.npmjs.com/package/axios)
- [react-icons](https://react-icons.github.io/react-icons/)
- [styled-components](https://styled-components.com/)
- [reactstrap](https://reactstrap.github.io/)
- [lodash](https://www.npmjs.com/package/lodash)
- [uuid](https://www.npmjs.com/package/uuid)

## NPM or Yarn
您可以使用npm或yarn来安装软件包。如果要使用[yarn](https://yarnpkg.com)，请单独安装。我建议您坚持使用其中一种包装。不要在一个应用程序中同时使用两个软件包管理工具。

让我们看看如何将软件包安装到应用程序。首先，我们进入项目目录并编写以下命令。

```sh
// syntax, we can use i or install
npm i package-name
// or
yarn add package-name
```

### node-sass

Sass是一个CSS预处理程序，它允许编写CSS函数，嵌套等等。让我们安装node-sass来利用Sass的功能。

使用 npm:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ npm install node-sass
```

使用 yarn:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ yarn add node-sass
```

安装node-sass之后，您可以在React中开始使用Sass。创建一个样式文件夹，并在此文件夹中创建test.scss。将此文件导入您正在使用的组件或index.js。您无需将node-sass导入组件。

```css
/* ./styles/header.scss */
header {
  background-color: #61dbfb;
  padding: 25;
  padding: 10px;
  margin: 0;
}
```

```js
// Header.js
import React from 'react'
import './styles/header.scss
const Header = () = (
   <header>
          <div className='header-wrapper'>
            <h1>30 Days Of React</h1>
            <h2>Getting Started React</h2>
            <h3>JavaScript Library</h3>
            <p>Instructor: Asabeneh Yetayeh</p>
            <small>Oct 15, 2020</small>
          </div>
        </header>
)

export default Header
```

```js
// App.js

import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import './styles/header.scss

class App extends Component {
  render() {
    return (
      <div className='App'>
       <Header />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### CSS 模块

除了Sass之外，最好知道如何在React中使用CSS模块。我们不必为CSS模块安装单独的软件包即可在React应用程序中使用CSS模块。CSS模块可以与Pure CSS或Sass一起使用。CSS模块的命名约定是一个特定的名称，后跟点和模块（test.module.css或test.module.scss）

命名:

```js
// naming for Sass
// naming for CSS
;[name].module.scss[name].module.css
```

```css
/* ./styles/header.module.scss */
.header {
  background-color: #61dbfb;
  padding: 25;
  padding: 10px;
  margin: 0;
}
.header-wrapper {
  font-weight:500
  border: 5px solid orange;
}
```

```js
// Header.js
import React from 'react'
import headerStyles from  './styles/header.module.scss
// We can all destructure the class name
const {header, headerWrapper} = headerStyles
const Header = () = (
   <header className = {headerStyles.header}>
          <div className={headerStyles.headerWrapper}>
            <h1>30 Days Of React</h1>
            <h2>Getting Started React</h2>
            <h3>JavaScript Library</h3>
            <p>Instructor: Asabeneh Yetayeh</p>
            <small>Oct 15, 2020</small>
          </div>
        </header>
)

export default Header
```

```js
// App.js

import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import './styles/header.scss

class App extends Component {
  render() {
    return (
      <div className='App'>
       <Header />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### axios

Axios是一个JavaScript库，可以发出HTTP请求以获取数据。在本节中，我们将在获取请求中看到。但是，可以使用[axios](https://github.com/axios/axios) 进行所有请求类型（GET，POST，PUT，PATCH，DELETE）。 

使用 npm:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ npm install axios
```

使用 yarn:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ yarn add axios
```

```js
import React, { Component } from 'react'
// axios is a package which
// send requests to a server to fetch data
import axios from 'axios'
import ReactDOM from 'react-dom'

class App extends Component {
  state = {
    data: [],
  }
  componentDidMount() {
    const API_URL = 'https://restcountries.eu/rest/v2/all'
    axios
      .get(API_URL)
      .then((response) => {
        this.setState({
          data: response.data,
        })
      })
      .catch((error) => {
        console.log(error)
      })
  }

  renderCountries = () => {
    return this.state.data.map((country) => {
      const languageOrLanguages =
        country.languages.length > 1 ? 'Langauges' : 'Language'
      const formatLanguages = country.languages
        .map(({ name }) => name)
        .join(', ')
      return (
        <div>
          <div>
            {' '}
            <img src={country.flag} alt={country.name} />{' '}
          </div>
          <div>
            <h1>{country.name}</h1>
            <p>Capital: {country.capital}</p>
            <p>
              {languageOrLanguages}: {formatLanguages}
            </p>
            <p>Population: {country.population}</p>
          </div>
        </div>
      )
    })
  }
  render() {
    return (
      <div className='App'>
        <h1>Fetching Data Using Axios</h1>
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

我们可以将axios与await和async函数一起使用。为了实现await和async，我们需要在componentDidMount之外具有单独的功能。如果我们实现了等待和异步，则必须通过try and catch处理错误

### react-icons

图标是网站的组成部分。获取不同的SVG图标

使用 npm:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ npm install react-icons
```

使用 yarn:

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react$ yarn add react-icons
```

```js
import React, { Component } from 'react'
import axios from 'axios'
import ReactDOM from 'react-dom'
import moment from 'moment'
import {
  TiSocialLinkedinCircular,
  TiSocialGithubCircular,
  TiSocialTwitterCircular,
} from 'react-icons/ti'

const Footer = () => (
  <footer>
    <h3>30 Days Of React</h3>
    <div>
      <TiSocialLinkedinCircular />
      <TiSocialGithubCircular />
      <TiSocialTwitterCircular />
    </div>
    <div>
      <small> Copyright &copy; {new Date().getFullYear()} </small>
    </div>
  </footer>
)

class App extends Component {
  render() {
    return (
      <div className='App'>
        <h1>Welcome to the world of Icons</h1>
        <Footer />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### moment

Moment 是一个小型JavaScript库，为我们提供了不同的时间格式。

```sh
npm install moment
```

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  render() {
    return (
      <div className='App'>
        <h1>How to use moment</h1>
        <p>This challenge was started {moment('2020-10-01').fromNow()}</p>
        <p>The challenge will be over in {moment('2020-10-30').fromNow()}</p>
        <p>Today is {moment(new Date()).format('MMMM DD, YYYY HH:mm')}</p>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### styled-components

它使用标记的模板文字来对组件进行样式设置。它删除了组件和样式之间的映射。这意味着当您定义样式时，实际上是在创建一个普通的React组件，并附加了样式。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import styled from 'styled-components'

const Title = styled.h1`
  font-size: 70px;
  font-weight: 300;
`
const Header = styled.header`
  background-color: #61dbfb;
  padding: 25;
  padding: 10px;
  margin: 0;
`

class App extends Component {
  render() {
    return (
      <div className='App'>
        <Header>
          <div>
            <Title>30 Days Of React</Title>
            <h2>Getting Started React</h2>
            <h3>JavaScript Library</h3>
            <p>Instructor: Asabeneh Yetayeh</p>
            <small>Oct 15, 2020</small>
          </div>
        </Header>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### reactstrap

 [reactstrap](https://reactstrap.github.io/) 允许使用bootstrap

### lodash

根据lodash的官方文档，“一个现代的JavaScript实用程序库提供了模块化，性能和附加功能。”

尝试还学习如何使用 _classnames_ 和 _validator_.

# 练习题

## 练习: Level 1

1. 什么是包?
2. 什么是第三方包 ?
3. 您必须使用第三方软件包吗?
4. 如何知道第三方软件包的流行性和稳定性?
5. npm上有多少个JavaScript软件包?
6. 您如何安装第三方软件包?
7. 您最常使用哪些软件包?
8. 您使用什么包来获取数据?
9. classnames这个包是用来干嘛的?
10. validator这个包是用来干嘛的?

## 练习: Level 2

1. 了解如何使用Sass
2. 了解如何使用axios
3. 了解如何使用 moment 和 react-icons
4. 使用 validator 来验证在第十二天写的表单
5. 使用 classnames 根据某些逻辑来更新.

## 练习: Level 3

🎉 CONGRATULATIONS ! 🎉

[<< 第十四天](../14_Day_Component_Life_Cycles/14_component_life_cycles-CN.md) | [第十六天 >>](../16_Higher_Order_Component/16_higher_order_component-CN.md)
