<div align="center">

   <h1> 30天学习React中文版</h1>
 
   翻译自 [30 Days Of React](https://github.com/Asabeneh/30-Days-Of-React)

</div>
<div>
<img align="right" width="100%"  src="./images/30_days_of_react.jpg" />
</div>



[第一天 >>](./01_Day_JavaScript_Refresher/01_javascript_refresher.md)

<span>因为第一天是JavaScript的基础，暂时没决定翻译</span>

| # Day |                                                           主题                                                            |
| ----- | :-------------------------------------------------------------------------------------------------------------------------: |
|00|[介绍](#介绍)<br>[依赖](#依赖) <br>[如何使用此库](#如何使用此库)<br> [安装](#安装)|
|01|[JavaScript 相关基础](./01_Day_JavaScript_Refresher/01_javascript_refresher.md)|
|02|[React入门](./02_Day_Introduction_to_React/02_introduction_to_react-CN.md)|
|03|[安装](./03_Day_Setting_Up/03_setting_up-CN.md)|
|04|[组件](./04_Day_Components/04_components-CN.md)|
|05|[Props](./05_Day_Props/05_props-CN.md)|
|06|[列表, Map and Keys](./06_Day_Map_List_Keys/06_map_list_keys-CN.md)|
|07|[类组件](./07_Day_Class_Components/07_class_components-CN.md)|
|08|[States](./08_Day_States/08_states-CN.md)|
|09|[条件渲染](./09_Day_Conditional_Rendering/09_conditional_rendering-CN.md)|
|10|[React文件结构](./10_React_Project_Folder_Structure/10_react_project_folder_structure-CN.md)|
|11|[事件](./11_Day_Events/11_events-CN.md)|
|12|[表单](./12_Day_Forms/12_forms-CN.md)|
|13|[受控组件和非受控组件](./13_Day_Controlled_Versus_Uncontrolled_Input/13_uncontrolled_input-CN.md)|
|14|[组件的生命周期](./14_Day_Component_Life_Cycles/14_component_life_cycles-CN.md)|
|15|[第三方库](./15_Third_Party_Packages/15_third_party_packages-CN.md)|
|16|[高阶组件](./16_Higher_Order_Component/16_higher_order_component-CN.md)|
|17|[React路由](./17_React_Router/17_react_router-CN.md)|
|18|[通过 Fetch和Axios获取数据](./18_Fetch_And_Axios/18_fetch_axios-CN.md)|
|19|[项目1](./19_projects/19_projects-CN.md)|
|20|[项目2](./20_projects/20_projects-CN.md)|
|21|[Hooks](./21_Introducing_Hooks/21_introducing_hooks-CN.md)|
|22|[表单使用Hooks](./22_Form_Using_Hooks/22_form_using_hooks-CN.md)|
|23|[使用Hooks获取数据](./23_Fetching_Data_Using_Hooks/23_fetching_data_using_hooks-CN.md)|
|24|[项目使用Hooks](./24_projects/24_projects-CN.md)|
|25|[自定义Hooks](./25_Custom_Hooks/25_custom_hooks-CN.md)|
|26|[Context](./26_Context/26_context.md)|
|27|[Ref](./27_Ref/27_ref.md)|
|28|[项目3](./28_project/28_project.md)|
|29|[探索](./29_explore/29_explore.md)|
|30|[结论](./30_conclusions/30_conclusions.md)|



🧡🧡🧡 享受编程 🧡🧡🧡
<div>


<small>

Support [*Asabeneh*](https://www.patreon.com/asabeneh?fan_landing=true) to create more educational materials</small> 

[<img src = './images/become_patreon.png' alt='become-asabeneh-patreon' title='click' />](https://www.patreon.com/asabeneh?fan_landing=true)  



</div>

---

- [介绍](#介绍)
- [依赖](#依赖)
- [如何使用此库](#如何使用此库)
  - [Star and Fork 这个库](#star-and-fork-这个库)
  - [Clone 到自己](#clone-到自己)
  - [创建新的分支](#创建新的分支)
  - [新建练习库](#新建练习库)
  - [提交练习库](#提交练习库)
  - [每天更新你的库](#每天更新你的库)
- [安装](#安装)
  - [安装NodeJS](#安装nodejs)
  - [浏览器](#浏览器)
    - [安装谷歌浏览器](#安装谷歌浏览器)
    - [打开谷歌浏览器开发者工具](#打开谷歌浏览器开发者工具)
    - [在浏览器的开发者工具组写代码](#在浏览器的开发者工具组写代码)
      - [打印](#打印)
      - [具有多个参数的Console.log](#具有多个参数的consolelog)
      - [注释](#注释)
      - [语法](#语法)
    - [算术运算](#算术运算)
  - [代码编辑器](#代码编辑器)
    - [安装Visual Studio Code](#安装visual-studio-code)
    - [如何使用Visual Studio Code](#如何使用visual-studio-code)

---

## 介绍

**恭喜你**决定参加30天的React编程挑战赛。在这个挑战中，您将学习开发React应用程序所需的一切。挑战结束时，您将获得30DaysOfReact编程挑战完成证书。如果您需要帮助或想帮助他人，可以加入 [telegram group](https://t.me/thirtydaysofreact).

**A 30DaysOfReact** 挑战是面向初学者以及高级JavaScript和React开发人员的指南。欢迎来到30天的React。React是一个JavaScript库。我喜欢使用和教React，也希望您也能这样做。在分步进行的30天的React挑战中，您将学习React，这是最受欢迎的用户界面JavaScript库之一。React可以完成JavaScript可以做的一切。React可用 **向网站添加交互性，以开发移动应用，桌面应用，游戏**.
我相信您将在接下来的30天内学到很多东西，并且您的编程和解决问题的能力也会得到显着提高。


 **我对有些地方就直接采用机翻来翻译，如果有读不懂的可以去看一下原文，我也是第一次去尝试边学习边翻译，如果大家有兴趣的话可以一起来学习，我也是乘机学习一次React，有写基础性的我就不翻译了，因为名词很难懂，这里作者还有一些30天学习的项目，如果想学习JavaScript的知识可以去学习 [30DaysOfJavaScript](https://github.com/Asabeneh/30-Days-Of-JavaScript) 这个项目**


## 依赖

为了与挑战相处，您需要具备以下条件：

1. 学习动力
2. 一台电脑
3. 互联网
4. 浏览器
5. IDE
6. HTML，CSS和JavaScript中级技能

## 如何使用此库

### Star and Fork 这个库

给我一个Star 或者 Fork这个库自己去学习把

### Clone 到自己

您应该始终直接从分支副本中进行工作

```bash
# note that an `ssh` link is used here, but an `https` link will work the same
git clone git@github.com:username/30-Days-Of-React.git
cd 30-Days-Of-React
```

### 创建新的分支

为了完成日常锻炼，我的建议是创建一个单独的分支来容纳您的锻炼文件夹或您进行的任何其他更改。这将使您的master分支始终保持干净，这意味着您的master始终与原始master相似。

```bash
git checkout -b exercise-solutions # `-b` creates the branch if it does not exist
```

### 新建练习库

在新分支中，您可以使用文件/文件夹来构建日常练习的解决方案

```bash
mkdir -p solutions/day-01 # `-p` helps create nested directories
touch solutions/day-01/level1.js # touch creates a file
```

### 提交练习库

将您的解决方案提交给你自己的Fork

```bash
git add solutions/day-01/level1.js
git commit -m "chore: exercise level1 complete"
git push origin exercise-solutions # branch `exercise-solutions` was created earlier
```

### 每天更新你的库

此仓库将在整个月中每天更新。当新的一天的内容可用时，您可以按照以下步骤更新您的分叉副本。

```bash
# 1. switch to master branch
git checkout master
# 2. check if your local copy has a link to original `...Asabeneh/30-Days-Of-React.git`
git remote -v
# 3. if not, add a link to original, you can choose any name for the link or use `upstream`
git remote add upstream git@github.com:Asabeneh/30-Days-Of-React.git
# 4. check again to confirm link added
git remote -v
# 5. now you can fetch updates from original repo, assuming you named this `upstream`
git fetch upstream
# 6. merge the updates to your local master branch
git merge upstream/master master
# 7. push the merged updates to your Forked copy on GitHub
git push origin master
```

> 请注意，更新仅应用于master分支。如果您希望更新任何其他分支，请使用分支名称重复步骤6-7。请参阅下面的代码段以获取`exercise-solutions`分支

```bash
git merge upstream/master exercise-solutions
git push origin exercise-solutions
```

## 安装

我相信您有成为开发人员，计算机和互联网的动力和强烈愿望。除了基本到中级的HTML，CSS和JS。如果您有这些，那么您就有一切开始

### 安装NodeJS

您现在可能不需要node.js，但以后可能需要它。安装[node.js](https://nodejs.org/en/).

![Node download](images/download_node.png)

下载后双击安装

![Install node](images/install_node.png)

我们可以通过打开设备终端或命令提示符来检查是否在本地计算机上安装了Node

```sh
asabeneh $ node -v
v12.14.0
```

在制作本教程时，我使用的是节点版本12.14.0，但是现在建议下载的node.js版本是12.17.0

### 浏览器

有许多浏览器。但是，我强烈建议您使用Google Chrome。

#### 安装谷歌浏览器

如果您还没有 [google chrome](https://www.google.com/chrome/)，请安装它。我们可以在浏览器控制台上编写小的JavaScript代码，但是我们不使用浏览器控制台来开发应用程序。

![Google Chrome](images/google_chrome.png)

#### 打开谷歌浏览器开发者工具

您可以通过单击浏览器右上角的三个点，然后选择“更多工具->开发者工具”或使用键盘快捷键来打开Goog​​le Chrome控制台。我更喜欢使用快捷方式。

![Opening chrome](images/opening_developer_tool.png)

使用键盘快捷键打开Chrome控制台。作为JavaScript和React开发人员，也应该知道快捷方式，您会在浏览器控制台上花费大量时间，并且在开发过程中不会懒于打开它。

```sh
Mac
Command+Option+J

Windows/Linux:
Ctl+Shift+J
```

![Opening console](images/opening_chrome_console_shortcut.png)

打开Goog​​le Chrome控制台后，尝试浏览标记的按钮。我们将大部分时间花在控制台上。控制台是您的JavaScript代码所在的地方。Google Console V8引擎将您的JavaScript代码更改为机器代码。让我们在Google Chrome控制台上编写JavaScript代码：

![write code on console](./images/js_code_on_chrome_console.png)

#### 在浏览器的开发者工具组写代码

我们可以在Google控制台或任何浏览器控制台上编写任何JavaScript代码。但是，对于这一挑战，我们仅关注Google Chrome控制台。使用以下命令打开控制台：

```sh
Mac
Command+Option+I

Windows:
Ctl+Shift+I
```

##### 打印

为了编写第一个JavaScript代码，我们使用了内置函数**console.log（）**。我们传递了一个参数作为输入数据，该函数显示了输出。我们在console.log（）函数中传递了“ Hello，World”作为输入数据或参数。

```js
console.log('Hello, World!')
```

##### 具有多个参数的Console.log

 **console.log()** 函数可以取多个参数分离由逗号。语法如下所示:**console.log(param1, param2, param3)**

![console log multiple arguments](./images/console_log_multipl_arguments.png)

```js
console.log('Hello', 'World', '!')
console.log('HAPPY', 'NEW', 'YEAR', 2020)
console.log('Welcome', 'to', 30, 'Days', 'Of', 'JavaScript')
```

从上面的代码段可以看出，console.log（）可以使用多个参数。建议使用尽可能多的console.log（）打印来检查代码中正在发生的事情，但不要永远在代码上保留所有console.log（）测试。保持浏览器控制台打开，使生活变得轻松。

##### 注释

我们在代码中添加注释。注释对于使代码更具可读性并在我们的代码中留下备注非常重要。JavaScript不会执行代码的注释部分，在JavaScript中，以//开头的任何文本行都是注释，而像/ * * /这样的内容也是注释。

**示例：单行注释**

//这是第一条注释
//这是第二条注释
//我是一行注释

**示例：多行注释**

/ *这是一个多行注释
多行注释可以占用多行
JavaScript是网络语言* /

##### 语法

编程语言与人类语言相似。英语或许多其他语言使用单词，短语，句子，复合句子及其他内容来传达有意义的信息。语法的英语含义是单词和短语的排列，以创建一种语言形式良好的句子。语法的技术定义是计算机语言中语句的结构。编程语言具有语法。JavaScript是一种编程语言，并且像其他编程语言一样，它具有自己的语法。如果我们没有编写JavaScript可以理解的语法，它将引发不同类型的错误。稍后我们将探讨各种JavaScript错误。现在，让我们看看语法错误

![Error](images/raising_syntax_error.png)

我故意犯了一个错误。结果，控制台引发语法错误。实际上，语法非常有用。它告知您犯了什么类型的错误。通过阅读错误反馈指南，我们可以更正语法并解决问题。从程序中识别和消除错误的过程称为调试。让我们修复错误：

```js
console.log("Hello, World!")
console.log('Hello, World!')
```

到目前为止，我们已经看到了如何使用console.log（）显示文本。如果我们使用console.log（）打印文本或字符串，则文本必须在单引号，双引号或反引号内
**示例:**

```js
console.log('Hello, World!')
console.log('Hello, World!')
console.log(`Hello, World!`)
```

#### 算术运算

现在，让我们练习更多使用google chrome控制台上的console.log（）编写数字数据类型的JavaScript代码。除了文本之外，我们还可以使用JavaScript进行数学计算。让我们进行以下简单计算。控制台可以直接使用参数，而无需**_console.log（）_**函数。但是，它包含在本简介中，因为大多数挑战将在文本编辑器中进行，在该文本编辑器中必须强制使用该功能。您可以直接按照控制台上的说明进行操作。

![Arithmetic](images/arithmetic.png)

```js
console.log(2 + 3) // Addition
console.log(3 - 2) // Subtraction
console.log(2 * 3) // Multiplication
console.log(3 / 2) // Division
console.log(3 % 2) // Modulus - finding remainder
console.log(3 ** 2) // Exponentiation 3 ** 2 == 3 * 3
```

### 代码编辑器

我们可以在浏览器控制台上编写代码，但不适用于较大的项目。在真实的工作环境中，开发人员使用不同的代码编辑器来编写他们的代码。在这30天的JavaScript挑战中，我们将使用Visual Studio Code

#### 安装Visual Studio Code

Visual Studio代码是一种非常流行的开源文本编辑器。我建议 [下载 Visual Studio Code](https://code.visualstudio.com/), 但是如果您赞成其他编辑器，请随时关注现有内容。

![Vscode](images/vscode.png)

如果您安装了Visual Studio Code，让我们开始使用它。

#### 如何使用Visual Studio Code

通过双击其图标打开Visual Studio代码。当您打开它时，您将获得这种界面。尝试与带有标签的图标进行交互。

![Vscode ui](./images/vscode_ui.png)

![Vscode add project](./images/adding_project_to_vscode.png)

![Vscode open project](./images/opening_project_on_vscode.png)

![script file](images/scripts_on_vscode.png)

![Installing Live Server](images/vsc_live_server.png)

![running script](./images/running_script.png)

![coding running](./images/launched_on_new_tab.png)

恭喜你！您已经完成了开始使用React所需的设置，但是在深入研究React之前，让我们做一个JavaScript复习。如果您对JavaScript非常满意，则可以跳过第一天的JavaScript复习。JavaScript复习部分内容丰富，可能需要一天以上的时间。根据我的经验，人们通常会被困在React中，因为他们的JavaScript知识很浅，因此，为了弥补这一空白，可在React的JavaScript复习部分中介绍可在React中使用的所有必需的JavaScript功能。有许多练习，但是您不需要解决它们。如果您想跳过JavaScript并直接跳入React，请单击[这里](../30-Days-Of-React/02_Day_Introduction_to_React/02_introduction_to_react-CN.md) 

🎉 CONGRATULATIONS ! 🎉

[第一天 >>](./01_Day_JavaScript_Refresher/01_javascript_refresher.md)
