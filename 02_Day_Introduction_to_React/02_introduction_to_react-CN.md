<div align="center">
  <h1> 30天学习React中文版</h1>
 
   翻译自 [30 Days Of React: Getting Started React](https://github.com/Asabeneh/30-Days-Of-React)

</div>

<span>前面课时因为是介绍是的JavaScript的基础知识，可以自己查看</span>

[<< 第一天](../01_Day_JavaScript_Refresher/01_javascript_refresher.md) | [第三天 >>](../03_Day_Setting_Up/03_setting_up.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_2.jpg)

- [React入门](#react入门)
  - [1. 什么是React?](#1-什么是react)
  - [2. 为什么使用React?](#2-为什么使用react)
    - [2020年10月React vs Vue 受欢迎程度](#2020年10月react-vs-vue-受欢迎程度)
    - [2020年2月React vs Vue 受欢迎程度](#2020年2月react-vs-vue-受欢迎程度)
  - [3. JSX](#3-jsx)
    - [JSX 元素](#jsx-元素)
    - [注释JSX元素](#注释jsx元素)
    - [渲染JSX元素](#渲染jsx元素)
    - [JSX中的样式和类名](#jsx中的样式和类名)
    - [将数据注入JSX元素](#将数据注入jsx元素)
      - [将字符串注入JSX元素](#将字符串注入jsx元素)
      - [Injecting a number to a JSX Element](#injecting-a-number-to-a-jsx-element)
      - [将数组注入JSX元素](#将数组注入jsx元素)
      - [将对象注入JSX元素](#将对象注入jsx元素)
  - [练习题](#练习题)
    - [练习：什么是React？](#练习什么是react)
    - [为什么是React?](#为什么是react)
    - [练习：JSX](#练习jsx)
    - [练习：JSX 元素](#练习jsx-元素)
    - [练习：内联样式](#练习内联样式)
    - [练习：内部风格](#练习内部风格)
    - [练习：将数据注入JSX](#练习将数据注入jsx)

## React入门

本节介绍了使用React的先决条件。您应该对以下技术有很好的了解：

- HTML
- CSS
- JavaScript

如果您具有上述技能，那么您将喜欢上React。“30天学习React"挑战包含您需要了解的有关React的所有信息。在每个部分中，都有一些练习和小型项目，建议您进行练习。这个30天的React挑战将帮助您逐步了解React的最新版本和旧版本。主题分为30天，其中每天包含几个主题，这些主题具有易于理解的解释，真实示例和许多动手练习。此挑战是为希望使用React和JavaScript构建Web应用程序的初学者和专业人士而设计的。有时您可能需要其他测试数据才能与React一起使用。您可以使用以下[测试数据生成器](https://www.30daysofreact.com/dummy-data)来生成不同的数据

### 1. 什么是React?

React是一个JavaScript库，用于构建可重用的用户界面（UI）。它最初于2013年5月29日发布。当前版本为16.13.1，某种程度上它是稳定的。React是由Facebook创建的。React使创建UI组件非常容易。官方的React文档可以在[中文社区](https://react.docschina.org/docs/getting-started.html)找到。当我们使用React时，我们不会直接与DOM交互。React有自己的方式来处理DOM（文档对象模型）操作。React使用其虚拟DOM进行新更改，并且仅更新需要更改的元素。在构建React应用程序并将DOM操作作业留给React虚拟DOM时，不要直接与DOM交互。在这个挑战中，我们将使用React开发10-15个Web应用程序。Web应用程序或网站由按钮，链接，具有不同输入字段的表单，页眉，页脚，部分，文章，文本，图像，音频，视频和不同形状的框组成。我们使用react来制作网站的可重用UI组件。

总结一下:

- React于2013年5月发布
- React由Facebook创建
- React是一个用于构建用户界面的JavaScript库
- React用于构建单页应用程序-一种只有一个HTML页面的应用程序.
- React允许我们创建可重用的UI组件
- React的最新版本是17.0.1
- [React 版本](https://react.docschina.org/versions)
- React官方文档可以在[中文社区](https://react.docschina.org/docs/getting-started.html) 找到

### 2. 为什么使用React?

React是最受欢迎的JavaScript库之一。最近几年，许多开发人员和公司都在使用它。它的受欢迎程度一直在快速增长，并且拥有庞大的社区。我们如何衡量人气？衡量普及程度的一种方法可能是GitHub repository stars, watchers and forks. 让我们比较一下 [React](https://github.com/facebook/react) 和 [Vue](https://github.com/vuejs/vue) 的受欢迎程度. 到今天为止，两种最流行的JavaScript之间的相似度如图所示。从图中，您可以推测出最受欢迎的JavaScript库。您可能会看到React和Vue的观察者，星号和叉子的数量。仅靠这些并不能很好地衡量其受欢迎程度，但仍然可以告诉我们这两种技术的受欢迎程度。如果我不得不在React旁边推荐另一个JavaScript库，那就是Vue.js。

#### 2020年10月React vs Vue 受欢迎程度

React 官方Git

![React Popularity October 2020](../images/react_repo_1_oct_2020.png)

Vue 官方Git

![Vue Popularity October 2020](../images/vue_repo_1_oct_2020.png)

#### 2020年2月React vs Vue 受欢迎程度

React 官方Git

![React Popularity February 2020](../images/react_popularity.png)

Vue 官方Git

![Vue Popularity February 2020](../images/vue_popularity.png)

为什么我们选择使用React？我们使用它的原因如下：

- 快速
- 模块化的
- 可扩展的
- 灵活
- 活跃的社区和受欢迎
- 开源的
- 广阔的工作机会

### 3. JSX

JSX代表JavaScript XML。JSX允许我们使用JavaScript代码编写HTML元素。HTML元素在开始标记中具有开始和结束标记，内容和属性。但是，某些HTML元素可能没有内容和结束标记-它们是自闭合元素。为了在React中创建HTML元素，我们不使用createElement（）而是使用JSX元素。因此，JSX使在React中编写和添加HTML元素变得更加容易。 JSX将使用 transpiler- [babel.js](https://babeljs.io/) 在浏览器上转换为JavaScript。Babel是一个将JSX转换为纯JavaScript以及将最新的JavaScript转换为较旧版本的库。请参见下面的JSX代码。

```js
// JSX syntax
// we don't need to use quotes with JSX

const jsxElement = <h1>I am a JSX element</h1>
const welcome = <h1>Welcome to 30 Days of React Challenge</h1>
const data = <small>Oct 2, 2020</small>
```

上面看起来很奇怪的代码看起来像JavaScript，看起来像，但是它不是JavaScript，看起来像HTML，但不完全是HTML元素。它是JavaScript和HTML元素的混合。JSX可以使我们在JavaScript中使用HTML。上面的JSX中的HTML元素是 _h1_ 和 _small_。

#### JSX 元素

如您在上面的示例中所看到的，JSX具有JavaScript和HTML之类的语法。JSX元素可以是单个HTML元素，也可以是包裹在父HTML元素中的许多HTML元素。

此JSX元素只有一个HTML元素，即 _h1_.

```js
const jsxElement = <h1>I am a JSX element</h1> // JS with HTML
```

让我们通过在 _h2_ 中声明一个名为title和content的新变量来制作更多JSX元素。

```js
const title = <h2>Getting Started React</h2>
```

让我们通过添加其他HTML元素来向此JSX元素添加字幕和其他内容。每个HTML元素都应由外部HTML元素包装，以创建有效的JSX元素。名称标题变量也应该更改为header，因为我们的JSX元素几乎包含了应用程序的所有标题

```js
const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
  </header>
)
```

让我们继续添加更多元素。显示作者姓名和年份的其他HTML元素。

```js
const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)
```

如您所见，_header_ 元素是所有内部HTML元素的父元素，并且JSX必须由外部父元素包装。如果没有 _标题_  HTML元素或其他父HTML元素，则上述JSX无效。

#### 注释JSX元素

我们出于各种原因对代码进行注释，并且知道如何在React中注释掉JSX元素也很不错。

```js
{
  /*
 <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>

*/
}
```

#### 渲染JSX元素

要将JSX元素呈现为HTML文档，我们首先应该创建一个索引HTML。index.html是您在任何React Application中将拥有的唯一HTML文件。这就是为什么我们说每个React Application是一个单页应用程序的原因。让我们创建一个index.html文件。我们可以通过两种方式开始使用React-通过使用CDN或create-react-app。create-react-app创建了一个React项目样板发件箱，因此，许多人确实很难理解React的工作方式。为了让绝对的初学者清楚明白，我想从CDN开始。我们仅在本节中使用CDN，在其余的挑战中我们将使用create-reap-app，并且我还建议您始终仅使用create-react-app。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script></script>
  </body>
</html>
```

从上面的index.html中可以看到，我们有一个 _div_，其中包含类根目录和脚本。root _div_ 是将所有React组件连接到index.html的网关。在script标签中，我们将编写JavaScript，但是script _type_ 将为 _babel_ 。Babel将在浏览器上将react JSX转换为纯JavaScript。让我们将babel添加到脚本中。在babel内部，我们可以编写任何纯JavaScript，JSX以及一般任何React代码

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // our code goes here
    </script>
  </body>
</html>
```
babel库已链接到我们的文档，现在我们可以使用它了。下一步是使用CDN或链接导入 _React_ 和 _ReactDOM_ 。为了链接React和ReactDOM，我们将CDN的两个包都附加到index.html的主体上。要测试React是否链接到index.html，请尝试通过console.log（React）进行检查。打开浏览器控制台，您应该得到一个对象。如果您看到一个包含React方法的对象，那么您就可以将项目与React CDN链接起来，并且可以使用React了。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      console.log(React)
    </script>
  </body>
</html>
```
现在index.html具有编写React代码所需的一切。让我们使用document.querySelect（'.root'）获得根元素，并将其分配给变量名称rootElement。这是我们直接与DOM进行交互的唯一位置。

现在，您知道了JSX和JSX元素。让我们在浏览器上呈现JSX元素，为此，我们需要React和ReactDOM库。除了React和ReactDOM之外，我们还需要babel将JSX转换为JavaScript代码。ReactDOM包有一个render方法。render方法带有两个参数：JSX元素或组件以及根文档。请参见下面的代码 [Code Pen](https://codepen.io/Asabeneh/full/JjdbjqK)。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')

      // JSX element
      const jsxElement = <h1>I am a JSX element</h1>

      // we render the JSX element using the ReactDOM package
      // ReactDOM has the render method and the render method takes two arguments
      ReactDOM.render(jsxElement, rootElement)
    </script>
  </body>
</html>
```

![Rendering JSX](../images/rendering_jsx.png)

让我们呈现更多内容。要呈现更多内容，JSX元素应具有更多HTML元素。例如，我们可以创建网站的标题，标题中可以包含标题，副标题，作者或日期等。请记住，我们一次只能渲染一个JSX元素 [Code Pen](https://codepen.io/Asabeneh/full/QWbGWeY)。
.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')

      // JSX element
      const header = (
        <header>
          <h1>Welcome to 30 Days Of React</h1>
          <h2>Getting Started React</h2>
          <h3>JavaScript Library</h3>
          <p>Asabeneh Yetayeh</p>
          <small>Oct 2, 2020</small>
        </header>
      )

      // we render the JSX element using the ReactDOM package
      // ReactDOM has the render method and the render method takes two arguments
      ReactDOM.render(header, rootElement)
    </script>
  </body>
</html>
```

![Rendering more content](../images/rendering_more_jsx_content_.png)

我们为网站的标题创建了一个JSX元素。网站的主要和页脚如何？与页眉类似，让我们为main和footer创建一个JSX元素。

网站主要部分的JSX元素。

```js
// JSX element
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
```

网站页脚部分的JSX元素。

```js
// JSX element
const footer = (
  <footer>
    <p>Copyright 2020</p>
  </footer>
)
```

现在，我们有了三个JSX元素：页眉，主要和页脚。呈现所有三个JSX元素的最佳方法是将它们全部包装在父JSX元素中或放置在数组中。要将JSX元素包含在另一个JSX元素内，我们使用大括号{}，并在大括号内调用JSX的名称。

```js
// JSX element for the header part of the website
const header = (
  <header>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)

// JSX element for the main part of the website
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

// JSX element for the footer part of the website
const footer = (
  <footer>
    <p>Copyright 2020</p>
  </footer>
)

// JSX element which contain all, it is a container or parent
const app = (
  <div>
    {header}
    {main}
    {footer}
  </div>
)
```

现在，让我们将所有内容放在一起并呈现到浏览器中。 [Code Pen](https://codepen.io/Asabeneh/full/MWwbYWg).

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')

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

      // we render the JSX element using the ReactDOM package
      // ReactDOM has the render method and the render method takes two argument
      ReactDOM.render(app, rootElement)
      // or
      //  ReactDOM.render([header, main, footer], rootElement)
    </script>
  </body>
</html>
```

![Rendering Multiple JSX Elements](../images/rendering_multiple_jsx_elements.png)

让我们对JSX元素应用一些样式，然后查看结果。

![Styling JSX Element](../images/styling_jsx_element.png).

现在，让我们将标头部分的样式仅应用 [Code Pen](https://codepen.io/Asabeneh/full/ZEGBYBG).

#### JSX中的样式和类名

到目前为止，我们尚未在JSX元素中应用任何样式。现在，让我们为JSX元素添加样式。在出现react之后，内联样式变得非常流行。让我们为header JSX元素添加边框。

要将样式添加到JSX元素，我们使用内联样式或className。我们使用{}注入样式对象。每个CSS属性都将成为键，并且每个CSS属性值都将成为该对象的值。例如，在下面的示例中，border是一个键，“ 2px纯橙色”是一个值，color是一个键，“ black”是一个值，fontSize是一个键，而“ 18px”是一个值。当我们在React或JavaScript的CSS对象中将这两个单词的CSS属性用作键时，所有这两个单词的CSS属性都将更改为camelCase。[Code Pen](https://codepen.io/Asabeneh/full/ZEGBYbY).

```js
const header = (
  <header
    style={{ border: '2px solid orange', color: 'black', fontSize: '18px' }}
  >
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)

// or we can write it this way

const style = { border: '2px solid orange', color: 'black', fontSize: '18px' }

const header = (
  <header style={style}>
    <h1>Welcome to 30 Days Of React</h1>
    <h2>Getting Started React</h2>
    <h3>JavaScript Library</h3>
    <p>Asabeneh Yetayeh</p>
    <small>Oct 2, 2020</small>
  </header>
)
```

好的做法是在开发应用程序时打开浏览器控制台，以了解一切是否顺利。

让我们继续设计所有已创建的JSX元素的样式：页眉，主要和页脚。我们还可以使用常规的内部样式来样式化我们的应用程序。使用常规样式，以HTML元素为目标，我们使用标签名称，id，类，属性和其他方法。这在React开发人员社区中很常见-人们使用类而不是id来大量使用。在本文中，我将仅使用类而不是id。

在JSX元素中，我们编写className而不是class，因为class是JavaScript中的保留字。与className类似，htmlFor代替了label标签中的for。请参见下面的示例。

```js
const title = <h1 className='title'>Getting Started React</h1>
const inputField = (
  <div>
    <label htmlFor='firstname'>First Name</label>
    <input type='text' id='firstname' placeholder='First Name' />
  </div>
)
```

输入元素中使用的id并非用于样式目的，而是用于将标签引用到输入字段。

如果使用class代替className或for代替htmlFor，您将看到这种警告。

![Class Name warning](../images/className_warning.png)

现在，您知道如何使用内联样式以及如何使用className。让我们设置所有JSX元素的样式。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>30 Days Of React Challenge</title>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')

      // style
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

      // we render the JSX element using the ReactDOM package
      ReactDOM.render(app, rootElement)
    </script>
  </body>
</html>
```

![Styling all JSX elements](../images/styling_all_jsx_elements.png)

使用常规样式方法代替样式对象比上面的方法更容易。现在，让我们使用内部样式来样式化所有JSX。也可以使用外部样式方法。 [Code Pen](https://codepen.io/Asabeneh/full/QWbGwge)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css?family=Montserrat:300,400,500|Roboto:300,400,500&display=swap"
      rel="stylesheet"
    />

    <title>30 Days Of React Challenge</title>
    <style>
      /* == General style === */
      * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
      }

      html,
      body {
        height: 100%;
        line-height: 1.5;
        font-family: 'Montserrat';
        font-weight: 300;
        color: black;
      }

      .root {
        min-height: 100%;
        position: relative;
      }

      .header-wrapper,
      .main-wrapper,
      .footer-wrapper {
        width: 85%;
        margin: auto;
      }

      .header-wrapper,
      .main-wrapper {
        padding: 10px;
        margin: 2px auto;
      }

      h1 {
        font-size: 70px;
        font-weight: 300;
      }

      h2,
      h3 {
        font-weight: 300;
      }

      header {
        background-color: #61dbfb;
        padding: 10px;
      }

      main {
        padding: 10px;
        padding-bottom: 60px;
        /* Height of the footer */
      }

      ul {
        margin-left: 15px;
      }

      ul li {
        list-style: none;
      }

      footer {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 60px;
        /* Height of the footer */
        background: #6cf;
      }

      .footer-wrapper {
        font-weight: 400;
        text-align: center;
        line-height: 60px;
      }
    </style>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')

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

      // we render the JSX element using the ReactDOM package
      ReactDOM.render(app, rootElement)
    </script>
  </body>
</html>
```

![Internal Style](../images/internal_style.png)

#### 将数据注入JSX元素

到目前为止，我们在JSX元素上使用了静态数据，但是我们也可以将不同的数据类型作为动态数据进行传递。动态数据可以是字符串，数字，布尔值，数组或对象。让我们逐步查看每种数据类型。要将数据注入JSX，我们使用{}括号。

```js
const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const authorFirstName = 'Asabeneh'
const authorLastName = 'Yetayeh'
const date = 'Oct 1, 2020'

// JSX element, header
const header = (
  <header>
    <div className='header-wrapper'>
      <h1>{welcome}</h1>
      <h2>{title}</h2>
      <h3>{subtitle}</h3>
      <p>
        Instructor: {authorFirstName} {authorLastName}
      </p>
      <small>Date: {date}</small>
    </div>
  </header>
)
```

与标头JSX元素相似，我们可以对主要和页脚JSX元素实施数据注入。

##### 将字符串注入JSX元素

在本节中，我们仅注入字符串

```js
const welcome = 'Welcome to 30 Days Of React'
const title = 'Getting Started React'
const subtitle = 'JavaScript Library'
const firstName = 'Asabeneh'
const lastName = 'Yetayeh'
const date = 'Oct 2, 2020'

// JSX element, header

// JSX element, header
const header = (
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
```

##### Injecting a number to a JSX Element

```js
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
const personAge = <p> {age}</p>
```

如您在上面的示例中看到的，可以进行一些算术计算和三元运算。

##### 将数组注入JSX元素

举一个数组的例子，让我们将HTML，CSS，JavaScript更改为数组并将其注入下面的主要JSX元素。我们将在稍后的“渲染列表”部分中更详细地介绍。

```js
const techs = ['HTML', 'CSS', 'JavaScript']

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
      <ul>{techs}</ul>
    </div>
  </main>
)
```

##### 将对象注入JSX元素

我们可以将字符串，数字，布尔值，数组数据注入JSX，但不能直接注入对象。在将数据注入JSX元素之前，我们应该首先提取对象值或对对象的内容进行解构。例如，让我们在一个对象内编写firstName和lastName并将其提取以在JSX中使用它们。

现在，让我们将所有内容放在一起。在这里，在下面的示例中，数据被动态注入到JSX中。 [Code Pen](https://codepen.io/Asabeneh/full/YzXWgpZ)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css?family=Montserrat:300,400,500|Roboto:300,400,500&display=swap"
      rel="stylesheet"
    />

    <title>30 Days Of React Challenge</title>
    <style>
      /* == General style === */
      * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
      }

      html,
      body {
        height: 100%;
        line-height: 1.5;
        font-family: 'Montserrat';
        font-weight: 300;
        color: black;
      }

      .root {
        min-height: 100%;
        position: relative;
      }

      .header-wrapper,
      .main-wrapper,
      .footer-wrapper {
        width: 85%;
        margin: auto;
      }

      .header-wrapper,
      .main-wrapper {
        padding: 10px;
        margin: 2px auto;
      }

      h1 {
        font-size: 70px;
        font-weight: 300;
      }

      h2,
      h3 {
        font-weight: 300;
      }

      header {
        background-color: #61dbfb;
        padding: 10px;
      }

      main {
        padding: 10px 10px 60px;
        /* Height of the footer */
      }

      ul {
        margin-left: 15px;
      }

      ul li {
        list-style: none;
      }

      footer {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 60px;
        /* Height of the footer */
        background: #6cf;
      }

      .footer-wrapper {
        font-weight: 400;
        text-align: center;
        line-height: 60px;
      }
    </style>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      // To get the root element from the HTML document
      const rootElement = document.querySelector('.root')
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
            <ul>{techs}</ul>
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

      // we render the JSX element using the ReactDOM package
      ReactDOM.render(app, rootElement)
    </script>
  </body>
</html>
```

![Dynamic Data](../images/dynamic_data.png)

如您所见，列表全都在一行中。因此，在将列表注入JSX之前，应该以所需的方式格式化列表。为了格式化列表，我们应该先修改数组，然后再将其注入JSX。我们可以使用map修改数组。作为一名React开发人员，您应该对函数式编程非常了解（映射，过滤，缩小，查找，每一个）。如果您对函数式编程不太了解，请查看第1天。

```js
const techs = ['HTML', 'CSS', 'JavaScript']
const techsFormatted = techs.map((tech) => <li>{tech}</li>)
```

在下面的代码示例中，列表现在包含列表元素，并且格式正确。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css?family=Montserrat:300,400,500|Roboto:300,400,500&display=swap"
      rel="stylesheet"
    />

    <title>30 Days Of React Challenge</title>
    <style>
      /* == General style === */
      * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
      }

      html,
      body {
        height: 100%;
        line-height: 1.5;
        font-family: 'Montserrat';
        font-weight: 300;
        color: black;
      }

      .root {
        min-height: 100%;
        position: relative;
      }

      .header-wrapper,
      .main-wrapper,
      .footer-wrapper {
        width: 85%;
        margin: auto;
      }

      .header-wrapper,
      .main-wrapper {
        padding: 10px;
        margin: 2px auto;
      }

      h1 {
        font-size: 70px;
        font-weight: 300;
      }

      h2,
      h3 {
        font-weight: 300;
      }

      header {
        background-color: #61dbfb;
        padding: 10px;
      }

      main {
        padding: 10px 10px 60px;
        /* Height of the footer */
      }

      ul {
        margin-left: 15px;
      }

      ul li {
        list-style: none;
      }

      footer {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 60px;
        /* Height of the footer */
        background: #6cf;
      }

      .footer-wrapper {
        font-weight: 400;
        text-align: center;
        line-height: 60px;
      }
    </style>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
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

      // we render the JSX element using the ReactDOM package
      ReactDOM.render(app, rootElement)
    </script>
  </body>
</html>
```

渲染清单

![List Id](../images/map_list_id.png)

如您在上方所见，现在列表已正确格式化，但是控制台上有一个警告，提示每个列表子项都应具有唯一的键。在数组中，我们没有id，但是当您在数据中有id时，通常会将id作为唯一值传递。现在，让我们为每个项目传递一个唯一的键以删除警告

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css?family=Montserrat:300,400,500|Roboto:300,400,500&display=swap"
      rel="stylesheet"
    />

    <title>30 Days Of React Challenge</title>
    <style>
      /* == General style === */
      * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
      }

      html,
      body {
        height: 100%;
        line-height: 1.5;
        font-family: 'Montserrat';
        font-weight: 300;
        color: black;
      }

      .root {
        min-height: 100%;
        position: relative;
      }

      .header-wrapper,
      .main-wrapper,
      .footer-wrapper {
        width: 85%;
        margin: auto;
      }

      .header-wrapper,
      .main-wrapper {
        padding: 10px;
        margin: 2px auto;
      }

      h1 {
        font-size: 70px;
        font-weight: 300;
      }

      h2,
      h3 {
        font-weight: 300;
      }

      header {
        background-color: #61dbfb;
        padding: 10px;
      }

      main {
        padding: 10px;
        padding-bottom: 60px;
        /* Height of the footer */
      }

      ul {
        margin-left: 15px;
      }

      ul li {
        list-style: none;
      }

      footer {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 60px;
        /* Height of the footer */
        background: #6cf;
      }

      .footer-wrapper {
        font-weight: 400;
        text-align: center;
        line-height: 60px;
      }
    </style>
  </head>

  <body>
    <div class="root"></div>

    <script
      crossorigin
      src="https://unpkg.com/react@16/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
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
      const currentYear = 2020
      const age = currentYear - yearBorn
      const personAge = (
        <p>
          {' '}
          {author.firstName} {author.lastName} is {age} years old
        </p>
      )

      // JSX element, main
      const techs = ['HTML', 'CSS', 'JavaScript']
      const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)

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

      // we render the JSX element using the ReactDOM package
      ReactDOM.render(app, rootElement)
    </script>
  </body>
</html>
```

![Removing the warning ](../images/removing_unique_id_warning.png)

现在，您对如何创建JSX元素以及如何将数据注入JSX有了很好的了解。在下一节中，我们将讨论如何使用create-react-app和组件。组件比JSX更强大和有用。

🌕 你太棒了。您刚刚完成了第二天的挑战，并且在迈向卓越的道路上前进了两个步骤。现在，为您的大脑和肌肉做一些运动

### 练习题

#### 练习：什么是React？

1. 什么是React？
2. 什么是 library?
3. 什么是单页应用程序?
4. 什么是 组件 ?
5. React的最新版本是什么?
6. 什么是DOM?
7. 什么是React Virtual DOM?
8. Web应用程序或网站（由其组成）具有什么?

#### 为什么是React?

1. 您为什么选择使用react?
2. 什么是衡量流行 ?
3. 最受欢迎的是React还是Vue ?

#### 练习：JSX

1. 什么是HTML元素
2. 如何编写完整HTML元素?
3. 什么是HTML属性？写一些
4. 什么是JSX?
5. 什么是babel?
6. 什么是转义器?

#### 练习：JSX 元素

1. 什么是JSX元素?
2. 将您的姓名写在JSX元素中，并将其存储在name变量中
3. 写一个JSX元素，显示您的全名，国家/地区，标题，性别，电子邮件，电话号码。将 _h1_ 用作名称，将 _p_ 用作其余信息，并将其存储在用户变量中
4. 写一个页脚JSX元素

#### 练习：内联样式

1. 主要JSX创建样式对象
2. 为页脚和应用JSX创建样式对象
3. 向JSX元素添加更多样式

#### 练习：内部风格

1. 将不同的样式应用于JSX元素

#### 练习：将数据注入JSX

1. 练习如何制作JSX元素并注入动态数据（字符串，数字，布尔值，数组，对象）

🎉 CONGRATULATIONS ! 🎉

[<< 第一天](../01_Day_JavaScript_Refresher/01_javascript_refresher.md) | [第三天 >>](../03_Day_Setting_Up/03_setting_up.md)
