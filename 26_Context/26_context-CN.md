<div align="center">
  <h1> 30 Days Of React: Context</h1>
</div>

[<< 第二十五天](../25_Custom_Hooks/25_custom_hooks-CN.md) | [第二十七天>>](../27_Ref/27_ref-CN.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_26.jpg)

# Context

Context 提供了一个无需为每层组件手动添加 props，就能在组件树间进行数据传递的方法。

在一个典型的 React 应用中，数据是通过 props 属性自上而下（由父及子）进行传递的，但这种做法对于某些类型的属性而言是极其繁琐的（例如：地区偏好，UI 主题），这些属性是应用程序中许多组件都需要的。Context 提供了一种在组件之间共享此类值的方式，而不必显式地通过组件树的逐层传递 props。


## 何时使用 Context

Context 设计目的是为了共享那些对于一个组件树而言是“全局”的数据，例如当前认证的用户、主题或首选语言。举个例子，在下面的代码中，我们通过一个 “theme” 属性手动调整一个按钮组件的样式

以上文字取自 [react 中文文档](https://react.docschina.org/docs/context.html) 没有任何更改。

看来react文档具有关于上下文的很好的信息，您可以阅读 [react 中文文档](https://react.docschina.org/docs/context.html).

# 练习

🎉 CONGRATULATIONS ! 🎉
[<< 第二十五天](../25_Custom_Hooks/25_custom_hooks-CN.md) | [第二十七天>>](../27_Ref/27_ref-CN.md)

