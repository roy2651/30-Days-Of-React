<div align="center">
  <h1> 30 Days Of React: Fetch and Axios</h1>
</div>

[<< 第十七天](../17_React_Router/17_react_router-CN.md) | [第十九天>>](../19_projects/19_projects-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_18.jpg)

- [Fetch and Axios](#fetch-and-axios)
  - [Fetch](#fetch)
  - [Axios](#axios)
- [练习题](#练习题)
  - [练习: Level 1](#练习-level-1)
  - [练习: Level 2](#练习-level-2)
  - [练习: Level 3](#练习-level-3)

# Fetch and Axios

## Fetch
当前，JavaScript提供了获取API来发出HTTP请求。并非所有浏览器都支持Fetch，因此我们安装了附加软件包以支持浏览器。但是，如果我们使用Axios，则不需要使用其他软件包来支持浏览器。Axios代码似乎比获取更整洁。在本节中，我们将看到fetch与axios之间的区别。可能是如果您想了解您在[caniuse](https://caniuse.com/ciu/index)网站上签到的获取的浏览器支持。截至今天，它具有95.62％的浏览器支持。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

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
  console.log(languages)
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
          {languages.map((language) => language.name).join(', ')}
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

class App extends Component {
  state = {
    data: [],
  }

  componentDidMount() {
    const url = 'https://restcountries.eu/rest/v2/all'
    fetch(url)
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        console.log(data)
        this.setState({
          data,
        })
      })
      .catch((error) => {
        console.log(error)
      })
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <Country country={country} />
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

我们可以实现异步和等待，并使上面的代码简短明了。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

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
  console.log(languages)
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
          {languages.map((language) => language.name).join(', ')}
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

class App extends Component {
  state = {
    data: [],
  }

  componentDidMount() {
    this.fetchCountryData()
  }

  fetchCountryData = async () => {
    const url = 'https://restcountries.eu/rest/v2/all'
    const response = await fetch(url)
    const data = await response.json()
    this.setState({
      data,
    })
  }

  render() {
    return (
      <div className='App'>
        <h1>Fetching API using Fetch</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <Country country={country} />
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如果我们使用async并等待，我们将使用try and catch处理错误。让我们在上面的代码中应用try catch块。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

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
        <p>
          <span>Currency: </span>
          {currency}
        </p>
      </div>
    </div>
  )
}

class App extends Component {
  state = {
    data: [],
  }

  componentDidMount() {
    this.fetchCountryData()
  }

  fetchCountryData = async () => {
    const url = 'https://restcountries.eu/rest/v2/all'
    try {
      const response = await fetch(url)
      const data = await response.json()
      this.setState({
        data,
      })
    } catch (error) {
      console.log(error)
    }
  }

  render() {
    return (
      <div className='App'>
        <h1>Fetching API using Fetch</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <Country country={country} />
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

现在，让我们看看如何使用axios进行相同的API调用。

如果我们有多个API两次调用怎么办

## Axios

Axios是第三方软件包，我们需要使用npm进行安装。这是发出HTTP请求（GET，POST，PUT，PATCH，DELETE）的最流行方法。在此示例中，我们将仅涵盖一个get请求。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import axios from 'axios'

const Country = ({
  country: { name, capital, flag, languages, population, currency },
}) => {
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
        >
      </div>
    </div>
  )
}

class App extends Component {
  state = {
    data: [],
  }

  componentDidMount() {
    const url = 'https://restcountries.eu/rest/v2/all'
    axios
      .get(url)
      .then((response) => {
        this.setState({
          data: response.data,
        })
      })
      .catch((error) => {
        console.log(error)
      })
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <Country country={country} />
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

我们还使用async和await实现axios的获取。

```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import axios from 'axios'

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

class App extends Component {
  state = {
    data: [],
  }

  componentDidMount() {
    this.fetchCountryData()
  }
  fetchCountryData = async () => {
    const url = 'https://restcountries.eu/rest/v2/all'
    try {
      const response = await axios.get(url)
      const data = await response.data
      this.setState({
        data,
      })
    } catch (error) {
      console.log(error)
    }
  }

  render() {
    return (
      <div className='App'>
        <h1>React Component Life Cycle</h1>
        <h1>Calling API</h1>
        <div>
          <p>There are {this.state.data.length} countries in the api</p>
          <div className='countries-wrapper'>
            {this.state.data.map((country) => (
              <Country country={country} />
            ))}
          </div>
        </div>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

如您所见，fetch和axios之间没有太大区别。但是由于浏览器支持和易用性，我建议您使用比获取更多的axios

# 练习题

## 练习: Level 1

1. 什么是HTTP请求？
2. 最常见的HTTP请求是什么？
3. 什么是fetch?
4. 什么是axios?
5. fetch 和 axios之间有什么区别?
6. 与axios相比，您是否更喜欢获取HTTP请求?

## 练习: Level 2

1. 在以下[API](https://api.thecatapi.com/v1/breeds)中找到猫的平均公制体重和寿命。API中有67种猫。

![Average cat weight and age](../images/average_cat_weight_and_age.png)

## 练习: Level 3

1. 多少个国家有猫科动物？
2. 哪个国家的猫品种最多？
3. 根据它们拥有的猫的数量按升序排列国家？

🎉 CONGRATULATIONS ! 🎉

[<< 第十七天](../17_React_Router/17_react_router-CN.md) | [第十九天>>](../19_projects/19_projects-CN.md)
