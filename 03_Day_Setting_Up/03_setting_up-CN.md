<div align="center">
  <h1> 30天学习React: 安装 </h1>
</div>

[<< 第二天](../02_Day_Introduction_to_React/02_introduction_to_react-CN.md) | [第四天 >>](../04_Day_Components/04_components-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_3.jpg)

- [安装](#安装)
  - [Node](#node)
  - [模块](#模块)
  - [包](#包)
  - [Node包管理工具(NPM)](#node包管理工具npm)
  - [Visual Studio Code](#visual-studio-code)
  - [浏览器](#浏览器)
  - [VS Code 扩展](#vs-code-扩展)
  - [创建React应用](#创建react应用)
- [您的第一个React App](#您的第一个react-app)
  - [React 脚手架](#react-脚手架)
  - [JSX中的样式](#jsx中的样式)
  - [将数据注入JSX元素](#将数据注入jsx元素)
  - [在React中导入媒体对象](#在react中导入媒体对象)
- [练习题](#练习题)
  - [练习：1层](#练习1层)
  - [练习：2层](#练习2层)
  - [练习：3层](#练习3层)

# 安装

上一节中，我们了解了JSX，并使用CDN访问了React和ReactDOM包。但是，在实际项目中，您将使用create-react-app软件包而不是CDN来生成React项目启动器（脚手架）。最初的 _create-react-app_ 于2016年7月22日发布。在此之前，开发人员曾经使用JavaScript模块捆绑器，babel和所有必需的软件包来手动配置webpack，这通常要花费半小时甚至更长的时间。现在，create-react-app将处理所有事情，您将只负责开发产品，而不用花费太多时间来配置和设置项目。在开始使用其他工具之前，让我们简要介绍一下我们将在此挑战中使用的所有工具。您不必了解所有内容，但是我将尝试简要介绍与React一起使用时所使用的一些工具和技术。

## Node

Node是一个JavaScript运行时环境，允许JavaScript在服务器上运行。Node创建于2009年。Node在JavaScript的增长中发挥了重要作用。默认情况下，React应用程序从localhost 3000启动。create-react-app已为React应用程序配置了一个节点服务器。这就是为什么我们需要节点和节点模块。我们将很快看到create-react-app

如果没有节点，请安装它。安装 [node.js](https://nodejs.org/en/).

![Node download](../images/download_node.png)

下载后双击安装

![Install node](../images/install_node.png)

我们可以通过打开设备终端或命令提示符并编写以下命令来检查本地计算机上是否安装了Nodejs:

```sh
asabeneh $ node -v
v12.18.0
```

## 模块

一个或多个功能（可以在需要时导出和导入）可以包含在项目中。在React中，我们不使用链接来访问模块或包，而是导入模块。让我们看看如何导入和导出一个或多个模块：

```js
// math.js
export const addTwo = (a, b) => a + b
export const multiply = (a, b) => a * b
export const subtract = (a, b) => a - b

export default (function doSomeMath() {
  return {
    addTwo,
    multiply,
    subtract,
  }
})()
```

现在让我们将math.js模块导入另一个文件：

```js
// index.js
// to import the doSomeMath from the math.js with or without extension
import doSomeMath from './math.js'

// to import the other modules
// since these modules were not exported as default we have to desctructure
import { addTwo, multiply, subtract } from './math.js'

import * as everything from './math.js' // to import everything remaining
console.log(addTwo(5, 5))
console.log(doSomeMath.addTwo(5, 5))
console.log(everything)
```

之后，当您看到从“react”导入 _React_ 或从“ react-dom”导入 _ReactDOM_ 时，您不会感到惊讶。


## 包

包是模块或模块集合。例如，React，ReactDOM是包。

## Node包管理工具(NPM)

NPM创建于2010年。您不需要单独安装NPM-安装节点时，您还将拥有NPM。NPM是Node.js的默认软件包管理器。它允许用户使用和分发注册表中可用的JavaScript模块。NPM允许创建软件包，使用软件包和分发软件包。NMP在JavaScript的增长中也起了很大的作用。当前，NPM注册表中有350,000多个软件包。让我们看看NPM注册表上的create-react-app。下载次数表明该软件包的受欢迎程度。

![NPM create-react-app](../images/npm_registry.png)

## Visual Studio Code

我们将使用Visual Studio Code作为代码编辑器。如果尚未安装并 [下载](https://code.visualstudio.com) 并安装.

## 浏览器

我们将使用谷歌浏览器

## VS Code 扩展

您可能需要从Visual Studio Code安装这些扩展

- Prettier
- ESLint
- Bracket Pair Colorizer
- ES7 React/Redux/GraphQL/React-Native snippets

## 创建React应用

创建一个React项目，您可以使用以下方法之一。假设您已安装节点。在Mac或Linux上打开命令行界面（CLI），git bash或终端。然后运行以下命令。我正在使用git bash。

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop
$ npx create-react-app name-of-your-project
```

如果您不想每次创建项目时都写npx，则可以使用以下命令在计算机中全局安装create-react-app软件包。

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop
$ npm install -g create-react-app
```

安装create-react-app后，您将创建一个React应用程序，如下所示：

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop
$ create-react-app name-of-project
```

# 您的第一个React App

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~
\$ cd Desktop/
```

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop
\$ npx create-react-app 30-days-of-react
```

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop
\$ cd 30-days-of-react/
```

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react (master)
\$ npm start
```

现在您的React应用程序应该在本地主机3000上运行。转到App.js并通过编写一些文本来修改内容，您将在浏览器上看到最新的更改。要停止服务器，请在命令行中按Ctr +C

![React Starting](../images/react_app_starting.png)

## React 脚手架

让我们看一下React框架，它是由create-react-app创建的。每当创建新项目时，都将运行create-react-app和项目名称。

在下面的React脚手架，有三个文件夹：node_modules，public和src。此外，还有.gitignore，README.md，package.json和yarn.lock。你们当中有些人可能没有package-lock.json，而是不是yarn.lock。

很开心认识这些文件夹和文件。

- node_modules - 存储React应用程序的所有必需的Node包.

- Public

  - index.html - 整个应用程序中唯一的HTML文件

  - favicon.ico - 图标文件
  - manifest.json - 用于使应用程序成为渐进式Web应用程序
  - other images - 开放图图像（开放图图像是当链接在社交媒体上共享时可见的图像）
  - robots.txt - 信息（如果网站允许网页抓取）

- src

  - App.css, index.css - 是不同的CSS文件
  - index.js - 一个允许将所有组件与index.html连接的文件
  - App.js - 我们通常在其中导入大多数演示组件的文件
  - serviceWorker.js: 用于添加渐进式Web应用程序功能
  - setupTests.js - 编写测试案例

- package.json- 应用程序使用的软件包列表
- .gitignore - .gitingore允许文件和文件夹不被推送到GitHub
- README.md - Markdown文件以编写文档
- yarn.lock or package-lock.json - 一种锁定软件包版本的方法

![React Boilerplate](../images/react_boilerplate.png)

现在，让我们删除当前不需要的所有文件，并仅保留我们现在需要的文件。

删除大多数文件后，样板的结构如下所示：

![React Boilerplate Cleaned](../images/react_bolier_plate_cleaned.png)

现在让我们在index.js上编写代码。首先，我们应该导入React和ReactDOM。React允许我们编写JSX和ReactDOM以便在DOM上呈现JSX。ReactDOM有一个render方法。让我们使用在第2天创建的所有JSX元素。ReactDOM渲染方法带有两个参数，一个JSX或一个组件以及root。

```js
//index.js
// importing the react and react-dom package

import React from 'react'
import ReactDOM from 'react-dom'

const jsxElement = <h1>This is a JSX element</h1>
const rootElement = document.getElementById('root')

ReactDOM.render(jsxElement, rootElement)
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link
      href="https://fonts.googleapis.com/css?family=Montserrat:300,400,500|Roboto:300,400,500&display=swap"
      rel="stylesheet"
    />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />

    <title>30 Days Of React App</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

如果您的应用程序未在运行，请转到您的项目文件夹并运行以下命令

```sh
Asabeneh@DESKTOP-KGC1AKC MINGW64 ~/Desktop/30-days-of-react (master)
\$ npm start
```

如果您没有任何错误，React应用程序将在浏览器上启动。

![JSX using create react app](../images/jsx_use_create_react_app.png)

让我们编写更多的JSX元素并在浏览器中呈现它们。此表达式是由h2 HTML元素组成的JSX元素。

```js
const title = <h2>Getting Started React</h2>
```

让我们向以前的JSX添加更多内容，并将名称更改为header。

```js
const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
  </header>
)
```

让我们将此呈现给浏览器，为此，我们需要ReactDOM。

```js
//index.js
// importing the react and react-dom package

import React from 'react'
import ReactDOM from 'react-dom'

const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)
const rootElement = document.getElementById('root')

ReactDOM.render(header, rootElement)
```

![JSX using create react app](../images/rendering_more_jsx_content_create_react_app.png)

现在，让我们添加在第2天创建的所有JSX。

```js
//index.js
// importing the react and react-dom package
import React from 'react'
import ReactDOM from 'react-dom'

// JSX element, header
const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)

// JSX element, main
const main = (
  <main>
    <p>Prerequisite to get started react.js:</p>
    <ul>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </ul>
  </main>
)

// JSX element, footer
const footer = (
  <footer>
    <p>Copyright 2020</p>
  </footer>
)

// JSX element, app, a container or a parent
const app = (
  <div>
    {header}
    {main}
    {footer}
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
// ReactDOM has the render method and the render method takes two argument
ReactDOM.render(app, rootElement)
// or
//  ReactDOM.render([header, main, footer], rootElement)
```

![JSX using create react app to render more jsx](../images/rendering_multiple_jsx_elements_create-react_app.png)

## JSX中的样式

让我们将样式应用于JSX元素。我们可以使用内联，内部或外部CSS样式来为JSX设置样式。现在，让我们将内联样式应用于每个JSX元素。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

const headerStyles = {
  backgroundColor: '#61DBFB',
  fontFamily: 'Helvetica Neue',
  padding: 25,
  lineHeight: 1.5,
}

// JSX element, header
const header = (
  <header style={headerStyles}>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Asabeneh Yetayeh</p>
      <small>Oct 2, 2020</small>
    </div>
  </header>
)

// JSX element, main
const mainStyles = {
  backgroundColor: '#F3F0F5',
}
const main = (
  <main style={mainStyles}>
    <p>Prerequisite to get started react.js:</p>
    <ul>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </ul>
  </main>
)

const footerStyles = {
  backgroundColor: '#61DBFB',
}
// JSX element, footer
const footer = (
  <footer style={footerStyles}>
    <p>Copyright 2020</p>
  </footer>
)

// JSX element, app
const app = (
  <div className='app'>
    {header}
    {main}
    {footer}
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(app, rootElement)
```

![Inline styling JSX](../images/styling_jsx_inline_create_react_app.png)

现在，让我们应用内部样式，我们将所有CSS放在index.html的标题中。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
// JSX element, header
const header = (
  <header>
    <div className='header-wrapper'>
      <h1>Welcome to 30 Days Of React</h1>
      <h2>Getting Started React</h2>
      <h3>JavaScript Library</h3>
      <p>Instructor: Asabeneh Yetayeh</p>
      <small>Date: Oct 1, 2020</small>
    </div>
  </header>
)

// JSX element, main
const main = (
  <main>
    <div className='main-wrapper'>
      <p>
        Prerequisite to get started{' '}
        <strong>
          <em>react.js</em>
        </strong>
        :
      </p>
      <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li> JavaScript</li>
      </ul>
    </div>
  </main>
)

// JSX element, footer
const footer = (
  <footer>
    <div className='footer-wrapper'>
      <p>Copyright 2020</p>
    </div>
  </footer>
)

// JSX element, app
const app = (
  <div className='app'>
    {header}
    {main}
    {footer}
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(app, rootElement)
```

![Inline styling JSX](../images/js_internal_style_create_react_app.png)

## 将数据注入JSX元素

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
// To get the root element from the HTML document

// JSX element, header
const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const author = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
}
const date = 'Oct 2, 2020'

// JSX element, header
const header = (
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
const currentYear = new Date().getFullYear()
const age = currentYear - yearBorn
const personAge = (
  <p>
    {' '}
    {author.firstName} {author.lastName} is {age} years old
  </p>
)

// JSX element, main
const techs = ['HTML', 'CSS', 'JavaScript']
const techsFormatted = techs.map((tech) => <li>{tech}</li>)

// JSX element, main
const main = (
  <main>
    <div className='main-wrapper'>
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
  </main>
)

const copyRight = 'Copyright 2020'

// JSX element, footer
const footer = (
  <footer>
    <div className='footer-wrapper'>
      <p>{copyRight}</p>
    </div>
  </footer>
)

// JSX element, app
const app = (
  <div className='app'>
    {header}
    {main}
    {footer}
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(app, rootElement)
```

![Inline styling JSX](../images/inecting_data_to_jsx_create_react_app.png)

## 在React中导入媒体对象

我们如何在React中导入图像，视频和音频？让我们看看我们如何首先导入图像。在src文件夹中创建images文件夹并将其保存在其中。例如，让我们保存asabeneh.jpg图像，然后将该图像导入index.js。导入后，我们将其注入到JSX表达式中，用户。请参见下面的代码。

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images/asabeneh.jpg'

const user = (
  <div>
    <img src={asabenehImage} alt='asabeneh image' />
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(user, rootElement)
```

![Rendering image](../images/rendering_image.png)

让我们将用户注入到主要的JSX元素中，然后查看结果:

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
// To get the root element from the HTML document
import asabenehImage from './images/asabeneh.jpg'
// JSX element, header
const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const author = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
}
const date = 'Oct 2, 2020'

// JSX element, header
const header = (
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
const currentYear = new Date().getFullYear()
const age = currentYear - yearBorn
const personAge = (
  <p>
    {' '}
    {author.firstName} {author.lastName} is {age} years old
  </p>
)

// JSX element, main
const techs = ['HTML', 'CSS', 'JavaScript']
const techsFormatted = techs.map((tech) => <li>{tech}</li>)

const user = (
  <div>
    <img src={asabenehImage} alt='asabeneh image' />
  </div>
)

// JSX element, main
const main = (
  <main>
    <div className='main-wrapper'>
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
      {user}
    </div>
  </main>
)

const copyRight = 'Copyright 2020'

// JSX element, footer
const footer = (
  <footer>
    <div className='footer-wrapper'>
      <p>{copyRight}</p>
    </div>
  </footer>
)

// JSX element, app
const app = (
  <div className='app'>
    {header}
    {main}
    {footer}
  </div>
)

const rootElement = document.getElementById('root')
// we render the JSX element using the ReactDOM package
ReactDOM.render(app, rootElement)
```

![All JSX together final](../images/all_jsx_final.png)

可在此处 [here](../03/../03_Day_Setting_Up/30-days-of-react_boilerplate)找到代码

# 练习题

## 练习：1层

1. 什么是模块?
2. 什么是包?
3. 模块和包装之间有什么区别。
4. 什么是NPM?
5. 什么是Webpack?
6. 您如何创建一个新的React项目？
7. 项目文件夹中的文件和文件夹是什么（package.json，package-lock.json或yarn.lock，.gitignore，node_modules和public）？
8. 您最喜欢的代码编辑器是什么（我相信它是Visual Studio Code）?
9. 添加不同的Visual Studio Code扩展以提高您的生产力(eg. prettier, ESLint etc).
10. 尝试在其他文件中创建一个不同的自定义模块，然后将其导入index.js.

## 练习：2层

1. 导入并渲染以下图像
   ![Front end](../images/frontend_technologies.png)

2. 使用h1，p，input和button HTML元素使用JSX创建以下设计

![News Letter](../images/news_letter_design.png)

## 练习：3层

1. 设计以下用户卡。

![User Card](../images/user_card_design_jsx.png)

🎉 CONGRATULATIONS ! 🎉

[<< 第二天](../02_Day_Introduction_to_React/02_introduction_to_react-CN.md) | [第四天 >>](../04_Day_Components/04_components-CN.md)
