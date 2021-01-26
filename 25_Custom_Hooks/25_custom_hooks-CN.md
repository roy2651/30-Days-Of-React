<div align="center">
  <h1> 30 Days Of React: 自定义Hooks</h1>

</div>

[<< 第二十四天](../24_projects/24_projects-CN.md) | [第二十六天>>](../26_Context/26_context-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_25.jpg)

# Custom Hooks

可以在可用的React Hooks上制作一个自定义hook。例如，当我们获取数据时，我们可以使用fetch或axios来发送HTTP请求，并使用Effect hook来管理React的生命周期。让我们在useEffect和useState之上构建useFetch自定义钩子。

我们在上一节中编写了此代码段，并使用useEffect hooks从API提取数据。现在，让我们将此代码转换为自定义Hooks。自定义Hooks的命名约定为camelCase，它以单词use开头，这就是为什么我们将自定义hooks useFetch命名的原因。

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

创建文件名useFetch.js，并导入useState和useEffect。然后将上述代码的状态，useEffect和fetchData函数部分传输到useFetch.js。

```js
import { useState, useEffect } from 'react'

const useFetch = () => {
  const [data, setData] = useState([])

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

  useEffect(() => {
    fetchData()
  }, [])
}
```

然后，让useFetch函数获取一个参数。当我们获取数据时，唯一改变的是API，因此让我们传递该函数的URL参数。

```js
import { useState, useEffect } from 'react'

const useFetch = (url) => {
  const [data, setData] = useState([])

  const fetchData = async () => {
    try {
      const response = await fetch(url)
      const data = await response.json()
      setData(data)
    } catch (error) {
      console.log(error)
    }
  }

  useEffect(() => {
    fetchData()
  }, [])
}

export default useFetch
```

使用上面的代码，我们应该设法获取数据，但是建议将函数放在useEffect中，让我们将函数代码移到useEffect中。

```js
import { useState, useEffect } from 'react'

export const useFetch = (url) => {
  const [data, setData] = useState([])

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url)
        const data = await response.json()
        setData(data)
      } catch (error) {
        console.log(error)
      }
    }
    fetchData()
  }, [url])

  return data
}

export default useFetch
```

现在，让我们结合一切并使其工作。

```js
// index.js

import React, { useState, useEffect } from 'react'
import axios from 'axios'
import ReactDOM, { findDOMNode } from 'react-dom'
import useFetch from './useFetch'

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
  const url = 'https://restcountries.eu/rest/v2/all'
  const data = useFetch(url)

  return (
    <div className='App'>
      <h1>Custom Hooks</h1>
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

useState和useEffect hooks是您日常使用的最常见的React hooks。除了基本的hooks，还有一些其他的hooks并不经常使用。您不必知道如何使用所有hooks。useState，useEffect和useRef是非常重要的钩子，建议您了解如何使用它们。
# 练习

注意：继续构建国家/地区应用程序

1 使用[countries API](https://restcountries.eu/rest/v2/all)构建以下应用程序
[DEMO](https://www.30daysofreact.com/day-23/countries-data)

🎉 CONGRATULATIONS ! 🎉

[<< 第二十四天](../24_projects/24_projects-CN.md) | [第二十六天>>](../26_Context/26_context-CN.md)
