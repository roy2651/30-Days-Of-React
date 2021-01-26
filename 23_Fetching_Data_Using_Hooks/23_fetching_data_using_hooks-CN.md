<div align="center">
  <h1> 30 Days Of React: 使用Hooks获取数据</h1>
</div>

[<< 第二十二天](../22_Form_Using_Hooks/22_form_using_hooks-CN.md) | [第二十四天>>](../24_projects/24_projects-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_23.jpg)

- [Introducing React Hook](#introducing-react-hook)
  - [Basic Hooks](#basic-hooks)
    - [State Hook](#state-hook)
    - [Effect Hook](#effect-hook)
    - [Context Hook](#context-hook)
  - [Additional Hook](#additional-hook)
- [Exercises](#exercises)
  - [Exercises: Level 1](#exercises-level-1)

# 使用Hooks获取数据

在前面的部分中，您学习了如何使用fetch和axios获取数据。在本节中，我们将使用useEffect hooks来获取数据。我们可以使用fetch或axios，但我更喜欢使用axios。在React hooks中，您不必单独使用componentDidMount生命周期来获取数据。useEffect包含了React生命周期方法（mounting, updating and unmounting）。让我们将在第18天编写的代码转换为React hooks。我们需要从react导入useEffect。useEffect接受的参数是回调和数组。如果数组为空，则其行为与componentDidMount生命周期相同，如果数组具有其他属性，则其行为也将与更新一样。

```js
import React, { useState, useEffect } from 'react'
import axios from 'axios'
import ReactDOM, { findDOMNode } from 'react-dom'

const Country = ({ country: { name, flag, population } }) => {
  return (
    <div className='country'>
      <div className='country_flag'>
        <img src={flag} alt={name} />
      </div>
      <h3 className='country_name'>{name.toUpperCase()}</h3>
      <div class='country_text'>
        <p>
          <span>Population: </span>
          {population}
        </p>
      </div>
    </div>
  )
}

const App = (props) => {
  // setting initial state and method to update state
  const [data, setData] = useState([])

  useEffect(() => {
    fetchData()
  }, [])

  const fetchData = async () => {
    const url = 'https://restcountries.eu/rest/v2/all'
    try {
      const response = await fetch(url)
      const data = await response.json()
      setData(data)
    } catch (error) {
      console.log(error)
    }
  }

  return (
    <div className='App'>
      <h1>Fetching Data Using Hook</h1>
      <h1>Calling API</h1>
      <div>
        <p>There are {data.length} countries in the api</p>
        <div className='countries-wrapper'>
          {data.map((country) => (
            <Country country={country} />
          ))}
        </div>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

# 练习

🎉 CONGRATULATIONS ! 🎉

[<< 第二十二天](../22_Form_Using_Hooks/22_form_using_hooks-CN.md) | [第二十四天>>](../24_projects/24_projects-CN.md)
