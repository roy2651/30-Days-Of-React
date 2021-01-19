<div align="center">
  <h1> 30 Days Of React: Mapping Arrays </h1>
</div>

[<< 第五天](./../05_Day_Props/05_props-CN.md) | [第七天 >>](../07_Day_Class_Components/07_class_components-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_6.jpg)

- [映射数组](#映射数组)
  - [映射和渲染数组](#映射和渲染数组)
    - [映射数字数组](#映射数字数组)
    - [映射数组](#映射数组-1)
    - [映射对象数组](#映射对象数组)
    - [键入映射数组](#键入映射数组)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [Exe练习rcises: Level 3](#exe练习rcises-level-3)

# 映射数组

数组是用于处理多种问题的最常用数据结构。在React中，我们通过将特定的HTML元素添加到数组的每个元素中，使用map来将数组修改为JSX列表

## 映射和渲染数组

大多数时候，数据采用数组或对象数组的形式。要在大多数情况下渲染此数组或对象数组，我们使用map修改数据。在上一节中，我们使用map方法绘制了技术人员列表。在本节中，我们将看到更多示例。

在以下示例中，您将看到我们如何在浏览器上呈现数字数组，字符串数组，国家/地区和技能数组。

```js
import React from 'react'
import ReactDOM from 'react-dom'
const App = () => {
  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        {[1, 2, 3, 4, 5]}
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如果您查看浏览器，将会看到数字以一行的形式连接在一起。为避免这种情况，我们修改了数组并将数组元素更改为JSX元素。参见下面的示例，该数组已修改为JSX元素列表。

### 映射数字数组

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Numbers = ({ numbers }) => {
  // modifying array to array of li JSX
  const list = numbers.map((number) => <li>{number}</li>)
  return list
}

// App component

const App = () => {
  const numbers = [1, 2, 3, 4, 5]

  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        <ul>
          <Numbers numbers={numbers} />
        </ul>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### 映射数组

让我们看看如何映射数组

```js
import React from 'react'
import ReactDOM from 'react-dom'

const skills = [
  ['HTML', 10],
  ['CSS', 7],
  ['JavaScript', 9],
  ['React', 8],
]

// Skill Component
const Skill = ({ skill: [tech, level] }) => (
  <li>
    {tech} {level}
  </li>
)

// Skills Component
const Skills = ({ skills }) => {
  const skillsList = skills.map((skill) => <Skill skill={skill} />)
  console.log(skillsList)
  return <ul>{skillsList}</ul>
}

const App = () => {
  return (
    <div className='container'>
      <div>
        <h1>Skills Level</h1>
        <Skills skills={skills} />
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### 映射对象数组

渲染对象数组

```js
import React from 'react'
import ReactDOM from 'react-dom'

const countries = [
  { name: 'Finland', city: 'Helsinki' },
  { name: 'Sweden', city: 'Stockholm' },
  { name: 'Denmark', city: 'Copenhagen' },
  { name: 'Norway', city: 'Oslo' },
  { name: 'Iceland', city: 'Reykjavík' },
]

// Country component
const Country = ({ country: { name, city } }) => {
  return (
    <div>
      <h1>{name}</h1>
      <small>{city}</small>
    </div>
  )
}

// countries component
const Countries = ({ countries }) => {
  const countryList = countries.map((country) => <Country country={country} />)
  return <div>{countryList}</div>
}
// App component
const App = () => (
  <div className='container'>
    <div>
      <h1>Countries List</h1>
      <Countries countries={countries} />
    </div>
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### 键入映射数组

Keys可帮助React识别已更改，添加或删除的项目。应该为数组内的元素提供键，以赋予元素稳定的身份。key应该是唯一的。大多数情况下，数据会以id的形式提供，我们可以将id用作键。如果我们在映射过程中未将key传递给React，它将在浏览器上发出警告。如果数据没有ID，则必须在映射时找到一种为每个元素创建唯一标识符的方法。请参见以下示例：

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Numbers = ({ numbers }) => {
  // modifying array to array of li JSX
  const list = numbers.map((num) => <li key={num}>{num}</li>)
  return list
}

const App = () => {
  const numbers = [1, 2, 3, 4, 5]

  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        <ul>
          <Numbers numbers={numbers} />
        </ul>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

我们还要在国家/地区映射示例中添加关键字。

```js
import React from 'react'
import ReactDOM from 'react-dom'

const countries = [
  { name: 'Finland', city: 'Helsinki' },
  { name: 'Sweden', city: 'Stockholm' },
  { name: 'Denmark', city: 'Copenhagen' },
  { name: 'Norway', city: 'Oslo' },
  { name: 'Iceland', city: 'Reykjavík' },
]

// Country component
const Country = ({ country: { name, city } }) => {
  return (
    <div>
      <h1>{name}</h1>
      <small>{city}</small>
    </div>
  )
}

// countries component
const Countries = ({ countries }) => {
  const countryList = countries.map((country) => (
    <Country key={country.name} country={country} />
  ))
  return <div>{countryList}</div>
}
const App = () => (
  <div className='container'>
    <div>
      <h1>Countries List</h1>
      <Countries countries={countries} />
    </div>
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

# 练习题

## 练习: Level 1

1. 什么需要映射数组？
2. 为什么在映射数组时需要键？
3. 解构代码的重要性是什么 ?
4. 解构是否使您的代码干净且易于阅读？

## 练习: Level 2

1. 在以下设计中，偶数为绿色，赔率为黄色，素数为红色。使用React组件构建以下颜色

![Number Generator](../images/day_6_number_generater_exercise.png)

2. 使用React组件创建以下十六进制颜色

![Number Generator](../images/day_6_hexadecimal_colors_exercise.png)

## Exe练习rcises: Level 3

1.使用给定的 [数据](../06_Day_Map_List_Keys/06_map_list_keys_boilerplate/src/data/ten_most_highest_populations.js) 制作条状图

![Ten most highest populations](../images/day_6_ten_highest_populations_exercise.png)

🎉 CONGRATULATIONS ! 🎉

[<< 第五天](./../05_Day_Props/05_props-CN.md) | [第七天 >>](../07_Day_Class_Components/07_class_components-CN.md)
