#   1、概述

- Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的**渐进式JavaScript框架**，发布于2014年2月。
- 与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。
- **Vue 的核心库只关注视图层**，方便与第三方库（如：`vue-router:跳转`，`vue-resource:通信`，`vuex:管理`)或既有项目整合。
- 官网：[https://cn.vuejs.org/v2/guide/](https://cn.vuejs.org/v2/guide/)

# 2、前端知识体系

想要成为真正的“互联网Java全栈工程师”还有很长的一段路要走，其中前端是绕不开的一门必修课。本阶段课程的主要目的就是带领Java后台程序员认识前端、了解前端、掌握前端，为实现成为“互联网Java全栈工程师”再向前迈进一步。

## 2.1、前端三要素

- HTML（结构）：超文本标记语言（Hyper Text Markup Language），决定网页的结构和内容
- CSS（表现）：层叠样式表（Cascading Style Sheets），设定网页的表现样式。
- JavaScript（行为）：是一种弱类型脚本语言，其源码不需经过编译，而是由浏览器解释运行，用于控制网页的行为

## 2.2、结构层（HTML）

略

## 2.3、表现层（CSS）

CSS层叠样式表是一门标记语言，并不是编程语言，因此不可以自定义变量，不可以引用等，换句话说就是不具备任何语法支持，它主要缺陷如下：

- 语法不够强大，比如无法嵌套书写，导致模块化开发中需要书写很多重复的选择器；
- 没有变量和合理的样式复用机制，使得逻辑上相关的属性值必须以字面量的形式重复输出，导致难以维护；
- 这就导致了我们在工作中无端增加了许多工作量。为了解决这个问题，前端开发人员会使用一种称之为**【CSS预处理器】**的工具,提供CSS缺失的样式层复用机制、减少冗余代码，提高样式代码的可维护性。大大的提高了前端在样式上的开发效率。

**什么是CSS预处理器**

CSS预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为CSS增加了一些编程的特性，将CSS作为目标生成文件，然后开发者就只需要使用这种语言进行CSS的编码工作。转化成通俗易懂的话来说就是“**用一种专门的编程语言，进行Web页面样式设计，再通过编译器转化为正常的CSS文件，以供项目使用”**。

常用的CSS预处理器有哪些

- SASS：基于Ruby ，通过服务端处理，功能强大。解析效率高。需要学习Ruby语言，上手难度高于LESS。
- LESS：基于NodeJS，通过客户端处理，使用简单。功能比SASS简单，解析效率也低于SASS，但在实际开发中足够了，所以如果我们后台人员如果需要的话，建议使用LESS。

## 2.4、行为层（JavaScript）

JavaScript一门弱类型脚本语言，其源代码在发往客户端运行之前不需要经过编译，而是将文本格式的字符代码发送给浏览器，由浏览器解释运行。
**Native 原生JS开发**
原生JS开发，也就是让我们按照【ECMAScript】标准的开发方式，简称ES，特点是所有浏览器都支持。截至到当前，ES标准以发布如下版本：

- ES3
- ES4（内部，未正式发布）
- ES5（全浏览器支持）
- ES6（常用，当前主流版本：webpack打包成为ES5支持）
- ES7
- ES8
- ES9（草案阶段）

区别就是逐步增加新特性。

**TypeScript 微软的标准**

- TypeScript是一种由微软开发的自由和开源的编程语言。它是JavaScript的一个超集， 而且本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。由安德斯·海尔斯伯格(C#、Delphi、TypeScript之父； .NET创立者) 主导。

- 该语言的特点就是除了具备ES的特性之外还纳入了许多不在标准范围内的新特性，所以会导致很多浏览器不能直接支持TypeScript语法， 需要编译后(编译成JS) 才能被浏览器正确执行。

### **JavaScript框架**

  - JQuery：大家熟知的JavaScript库，优点就是简化了DOM操作，缺点就是DOM操作太频繁，影响前端性能；在前端眼里使用它仅仅是为了兼容IE6，7，8；
  - Angular：Google收购的前端框架，由一群Java程序员开发，其特点是将后台的MVC模式搬到了前端并增加了**模块化开发**的理念，与微软合作，采用了TypeScript语法开发；对后台程序员友好，对前端程序员不太友好；最大的缺点是版本迭代不合理（如1代–>2 代，除了名字，基本就是两个东西；截止发表博客时已推出了Angular6）
  - React：Facebook 出品，一款高性能的JS前端框架；特点是提出了新概念 【虚拟DOM】用于减少真实 DOM 操作，在内存中模拟 DOM操作，有效的提升了前端渲染效率；缺点是使用复杂，因为需要额外学习一门【JSX】语言；
  - <font color=red>Vue</font>：一款渐进式 JavaScript 框架，所谓渐进式就是逐步实现新特性的意思，如实现模块化开发、路由、状态管理等新特性。其特点是综合了 Angular（模块化）和React(虚拟 DOM) 的优点；
  - <font color=red>Axios</font>：前端通信框架；因为 Vue 的边界很明确，就是为了处理 DOM，所以并不具备通信能力，此时就需要额外使用一个通信框架与服务器交互；当然也可以直接选择使用jQuery 提供的AJAX 通信功能；

### UI框架

  - Ant-Design：阿里巴巴出品，基于React的UI框架
  - ElementUI、iview、ice：饿了么出品，基于Vue的UI框架
  - BootStrap：Teitter推出的一个用于前端开发的开源工具包
  - AmazeUI：又叫“妹子UI”，一款HTML5跨屏前端框架

### JavaScript构建工具

  - Babel：JS编译工具，主要用于浏览器不支持的ES新特性，比如用于编译TypeScript
  - WebPack：模块打包器，主要作用就是打包、压缩、合并及按序加载

## 2.5、三端同一

### 混合开发（Hybrid App）

主要目的是实现一套代码三端统一（PC、Android：.apk、iOS：.ipa）并能够调用到设备底层硬件（如：传感器、GPS、摄像头等），打包方式主要有以下两种：

- 云打包：HBuild -> HBuildX，DCloud 出品；API Cloud
- 本地打包： Cordova（前身是 PhoneGap）

### 微信小程序

详见微信官网，这里就是介绍一个方便微信小程序UI开发的框架：WeUI

## 2.6、后端技术

前端人员为了方便开发也需要掌握一定的后端技术但我们Java后台人员知道后台知识体系极其庞大复杂，所以为了方便前端人员开发后台应用，就出现了Node JS这样的技术。

Node JS的作者已经声称放弃Node JS(说是架构做的不好再加上笨重的node modules，可能让作者不爽了吧)开始开发全新架构的De no

既然是后台技术，那肯定也需要框架和项目管理工具， Node JS框架及项目管理工具如下：

- Express：Node JS框架
- Koa：Express简化版
- NPM：项目综合管理工具，类似于Maven
- YARN：NPM的替代方案，类似于Maven和Gradle的关系

## 2.7、主流前端框架

### Vue.js

### **iView**， 有很多实用的基础组件比element ui的组件更丰富， 主要服务于PC界面的中后台产品。使用单文件的Vue组件化开发模式基于npm+webpack+babel开发， 支持ES 2015高质量、功能丰富友好的API， 自由灵活地使用空间。

- [官网地址](https://iviewui.com/)
- [Github](https://github.com/iview/iview)
- [iview-admin](https://www.worldlink.com.cn/en/osdir/iview-admin.html)

**备注：属于前端主流框架，选型时可考虑使用，主要特点是移动端支持较多**

### Element UI

Element是饿了么前端开源维护的Vue UI组件库， 组件齐全， 基本涵盖后台所需的所有组件，文档讲解详细， 例子也很丰富。主要用于开发PC端的页面， 是一个质量比较高的Vue UI组件库。

- [官网地址](https://element.eleme.io/)
- [Github](https://github.com/ElemeFE/element)
- [vue-element-admin](https://panjiachen.github.io/vue-element-admin-site/zh/)

**备注：属于前端主流框架，选型时可考虑使用，主要特点是桌面端支持较多**

### ICE

飞冰是阿里巴巴团队基于React/Angular/Vue的中后台应用解决方案， 在阿里巴巴内部， 已经有270多个来自几乎所有BU的项目在使用。飞冰包含了一条从设计端到开发端的完整链路，帮助用户快速搭建属于自己的中后台应用。

- [官网地址](https://ice.work/)

- [Github](https://github.com/alibaba/ice)

**备注：主要组件还是以React为主， 截止2019年02月17日更新博客前对Vue的支持还不太完善，目前尚处于观望阶段**

### VantUI

Vant UI是有赞前端团队基于有赞统一的规范实现的Vue组件库， 提供了-整套UI基础组件和业务组件。通过Vant， 可以快速搭建出风格统一的页面，提升开发效率。

- [官网地址](https://youzan.github.io/vant-weapp/#/intro)
- [Github](https://github.com/youzan/vant)

### AtUI

at-ui是一款基于Vue 2.x的前端UI组件库， 主要用于快速开发PC网站产品。它提供了一套n pm+web pack+babel前端开发工作流程， CSS样式独立， 即使采用不同的框架实现都能保持统一的UI风格。

- [官网地址]([https://at.aotu.io](https://at.aotu.io/))
- [Github](https://github.com/aliqin/atui)

### Cube Ul

cube-ui是滴滴团队开发的基于Vue js实现的精致移动端组件库。支持按需引入和后编译， 轻量灵活；扩展性强，可以方便地基于现有组件实现二次开发。

- [官网地址](http://www.cubeent.co.kr/)
- [Github](https://github.com/aliqin/atui)

### 混合开发

#### Flutter

Flutter是谷歌的移动端UI框架， 可在极短的时间内构建Android和iOS上高质量的原生级应用。Flutter可与现有代码一起工作， 它被世界各地的开发者和组织使用， 并且Flutter是免费和开源的。

- [官网地址](https://flutterchina.club/)
- [Github](https://github.com/flutter/flutter)

**备注：Google出品， 主要特点是快速构建原生APP应用程序， 如做混合应用该框架为必选框架**

#### lonic

lonic既是一个CSS框架也是一个Javascript UI库， lonic是目前最有潜力的一款HTML 5手机应用开发框架。通过SASS构建应用程序， 它提供了很多UI组件来帮助开发者开发强大的应用。它使用JavaScript MV VM框架和Angular JS/Vue来增强应用。提供数据的双向绑定， 使用它成为Web和移动开发者的共同选择。

- [官网地址](https://ionicframework.com/)
- [官网文档](http://www.ionic.wang/js_doc-index.html)
- [Github](https://github.com/flutter/flutter)

### 微信小程序

#### mpvue

mpvue是美团开发的一个使用`Vue.js`开发小程序的前端框架， 目前支持微信小程序、百度智能小程序，头条小程序和支付宝小程序。框架基于`Vue.js`， 修改了的运行时框架`runtime`和代码编译器`compiler`实现， 使其可运行在小程序环境中， 从而为小程序开发引入了`Vue.js`开发体验。

- [官网地址](http://mpvue.com/)
- [Git hub](https://github.com/Meituan-Dianping/mpvue)

**备注：完备的Vue开发体验， 井且支持多平台的小程序开发， 推荐使用**

#### WeUI

WeUI是一套同微信原生视觉体验一致的基础样式库， 由微信官方设计团队为微信内网页和微信小程序量身设计， 令用户的使用感知更加统一。包含button、cell、dialog、toast、article、icon等各式元素。

- [官网地址](https://weui.io/)
- [Git hub](https://github.com/Meituan-Dianping/mpvue)

# 3、了解前后分离的演变史

为什么需要前后分离为了降低开发的复杂度， 以后端为出发点， 比如：Struts、Spring MVC等框架的使用， 就是后端的MVC时代；
以`SpringMVC`流程为例：

![1595237159379](typora图片/1595237159379.png)

- 发起请求到前端控制器(`Dispatcher Servlet`)
- 前端控制器请求`HandlerMapping`查找`Handler`，可以根据`xml`配置、注解进行查找
- 处理器映射器`HandlerMapping`向前端控制器返回`Handler`
- 前端控制器调用处理器适配器去执行`Handler`
- 处理器适配器去执行`Handler`
- `Handler`执行完成给适配器返回`ModelAndView`
- 处理器适配器向前端控制器返回`ModelAndView`，`ModelAndView`是`SpringMvc`框架的一个底层对象，包括`Model`和`View`
- 前端控制器请求视图解析器去进行视图解析，根据逻辑视图名解析成真正的视图(`JSP`)
- 视图解析器向前端控制器返回`View`
- 前端控制器进行视图渲染，视图渲染将模型数据(在`ModelAndView`对象中)填充到`request`域
- 前端控制器向用户响应结果

**优点**

- MVC是一个非常好的协作模式， 能够有效降低代码的耦合度从架构上能够让开发者明白代码应该写在哪里。为了让View更纯粹， 还可以使用Thyme leaf、Frree marker等模板引擎， 使模板里无法写入Java代码， 让前后端分工更加清晰。

**缺点**

- 前端开发重度依赖开发环境，开发效率低，这种架构下，前后端协作有两种模式：
  - 第一种是前端写DEMO， 写好后， 让后端去套模板。好处是DEMO可以本地开发， 很高效。不足是还需要后端套模板，有可能套错，套完后还需要前端确定，来回沟通调整的成本比较大；
  - 另一种协作模式是前端负责浏览器端的所有开发和服务器端的View层模板开发。好处是UI相关的代码都是前端去写就好，后端不用太关注，不足就是前端开发重度绑定后端环境，环境成为影响前端开发效率的重要因素。
- 前后端职责纠缠不清：模板引擎功能强大，依旧可以通过拿到的上下文变量来实现各种业务逻辑。这样，只要前端弱势一点，往往就会被后端要求在模板层写出不少业务代码，还有一个很大的灰色地带是`Controller`， 页面路由等功能本应该是前端最关注的， 但却是由后端来实现。`Controller`本身与`Model`往往也会纠缠不清，看了让人咬牙的业务代码经常会出现在`Controller`层。这些问题不能全归结于程序员的素养， 否则JSP就够了。
- 对前端发挥的局限性：性能优化如果只在前端做空间非常有限，于是我们经常需要后端合作，但由于后端框架限制，我们很难使用**【Comet】**、**【Big Pipe】**等技术方案来优化性能。



**注：在这期间(2005年以前) ， 包括早期的JSP、PHP可以称之为Web 1.0时代。在这里想说一句， 如果你是一名Java初学者， 请你不要再把一些陈旧的技术当回事了， 比如JSP， 因为时代在变、技术在变、什么都在变(引用扎克伯格的一句话：唯一不变的是变化本身)；当我们去给大学做实训时，有些同学会认为我们没有讲什么干货，其实不然，只能说是你认知里的干货对于市场来说早就过时了而已**

## 3.2、基于AJAX带来的SPA时代

时间回到2005年`AJAX`(Asynchronous JavaScript And XML， 异步JavaScript和XML，老技术新用法)被正式提出并开始使用`CDN`作为静态资源存储， 于是出现了JavaScript王者归来(在这之前JS都是用来在网页上贴狗皮膏药广告的) 的SPA(Single Page Application) 单页面应用时代。

![1595237421062](typora图片/1595237421062.png)

**优点**
这种模式下， **前后端的分工非常清晰， 前后端的关键协作点是AJAX接口。**看起来是如此美妙， 但回过头来看看的话， 这与JSP时代区别不大。复杂度从服务端的JSP里移到了浏览器的JavaScript，浏览器端变得很复杂。类似Spring MVC， **这个时代开始出现浏览器端的分层架构**：

![1595237457081](typora图片/1595237457081.png)

缺点

- **前后端接口的约定**：如果后端的接口一塌糊涂，如果后端的业务模型不够稳定，那么前端开发会很痛苦；不少团队也有类似尝试，通过接口规则、接口平台等方式来做。**有了和后端一起沉淀的接口规则，还可以用来模拟数据，使得前后端可以在约定接口后实现高效并行开发。**
- 前端开发的复杂度控制：SPA应用大多以功能交互型为主，JavaScript代码过十万行很正常。大量JS代码的组织，与View层的绑定等，都不是容易的事情。

## 3.3、前端为主的MVC时代

此处的MVC模式如下：

- MVC(同步通信为主) ：Model、View、Controller
- MVP(异步通信为主) ：Model、View、Presenter
- MVVM(异步通信为主)：Model、View、View Model为了降低前端开发复杂度，涌现了大量的前端框架，比如：`Angular JS`、`React`、`Vue.js`、`Ember JS`等， 这些框架总的原则是先按类型分层， 比如Templates、Controllers、Models， 然后再在层内做切分，如下图：

![1595237632332](typora图片/1595237632332.png)

**优点**

- **前后端职责很清晰**：前端工作在浏览器端，后端工作在服务端。清晰的分工，可以让开发并行，测试数据的模拟不难， 前端可以本地开发。后端则可以专注于业务逻辑的处理， 输出RESTful等接口。
- **前端开发的复杂度可控**：前端代码很重，但合理的分层，让前端代码能各司其职。这一块蛮有意思的，简单如模板特性的选择，就有很多很多讲究。并非越强大越好，限制什么，留下哪些自由，代码应该如何组织，所有这一切设计，得花一本书的厚度去说明。
- **部署相对独立**：可以快速改进产品体验

**缺点**

- 代码不能复用。比如后端依旧需要对数据做各种校验，校验逻辑无法复用浏览器端的代码。如果可以复用，那么后端的数据校验可以相对简单化。
- 全异步， 对SEO不利。往往还需要服务端做同步渲染的降级方案。
- 性能并非最佳，特别是移动互联网环境下。
- SPA不能满足所有需求， 依旧存在大量多页面应用。URL Design需要后端配合， 前端无法完全掌控。

## 3.4、Node JS带来的全栈时代

前端为主的MVC模式解决了很多很多问题， 但如上所述， 依旧存在不少不足之处。随着Node JS的兴起， JavaScript开始有能力运行在服务端。这意味着可以有一种新的研发模式：

![1595237863311](typora图片/1595237863311.png)

在这种研发模式下，前后端的职责很清晰。对前端来说，两个UI层各司其职：

- Front-end Ul layer处理浏览器层的展现逻辑。通过CSS渲染样式， 通过JavaScript添加交互功能， HTML的生成也可以放在这层， 具体看应用场景。
- Back-end Ul layer处理路由、模板、数据获取、Cookie等。通过路由， 前端终于可以自主把控URL Design， 这样无论是单页面应用还是多页面应用， 前端都可以自由调控。后端也终于可以摆脱对展现的强关注，转而可以专心于业务逻辑层的开发。



通过Node， WebServer层也是JavaScript代码， 这意味着部分代码可前后复用， 需要SEO的场景可以在服务端同步渲染，由于异步请求太多导致的性能问题也可以通过服务端来缓解。前一种模式的不足，通过这种模式几乎都能完美解决掉。

与JSP模式相比， 全栈模式看起来是一种回归， 也的确是一种向原始开发模式的回归， 不过是一种螺旋上升式的回归。



基于Node JS的全栈模式， 依旧面临很多挑战：

- 需要前端对服务端编程有更进一步的认识。比如TCP/IP等网络知识的掌握。
- Node JS层与Java层的高效通信。Node JS模式下， 都在服务器端， RESTful HTTP通信未必高效， 通过SOAP等方式通信更高效。一切需要在验证中前行。
- 对部著、运维层面的熟练了解，需要更多知识点和实操经验。
- 大量历史遗留问题如何过渡。这可能是最大最大的阻力。
  **注：看到这里，相信很多同学就可以理解，为什么我总在课堂上说：“前端想学后台很难，而我们后端程序员学任何东西都很简单”；就是因为我们后端程序员具备相对完善的知识体系。**
- **全栈！So Easy！**



# 4、MVVM

## 1、什么是MVVM

  MVVM（Model-View-ViewModel）是一种软件设计模式，由微软WPF（用于替代WinForm，以前就是用这个技术开发桌面应用程序的）和Silverlight（类似于Java Applet，简单点说就是在浏览器上运行WPF）的架构师Ken Cooper和Ted Peters开发，是一种简化用户界面的**事件驱动编程方式**。由John Gossman（同样也是WPF和Sliverlight的架构师）与2005年在他的博客上发表。

  MVVM源自于经典的MVC（Model-View-Controller）模式。MVVM的核心是ViewModel层，负责转换Model中的数据对象来让数据变得更容易管理和使用。其作用如下：

- 该层向上与视图层进行双向数据绑定
- 向下与Model层通过接口请求进行数据交互

​        MVVM已经相当成熟了，主要运用但不仅仅在网络应用程序开发中。当下流行的MVVM框架有`Vue.js`，`Anfular JS`

## 2、为什么要使用MVVM

  MVVM模式和MVC模式一样，主要目的是分离视图（View）和模型（Model），有几大好处

- **低耦合**：视图（View）可以独立于Model变化和修改，一个ViewModel可以绑定到不同的View上，当View变化的时候Model可以不变，当Model变化的时候View也可以不变。
- **可复用**：你可以把一些视图逻辑放在一个ViewModel里面，让很多View重用这段视图逻辑。
- **独立开发**：开发人员可以专注于业务逻辑和数据的开发（ViewMode），设计人员可以专注于页面设计。
- **可测试**：界面素来是比较难以测试的，而现在测试可以针对ViewModel来写。

![1595238643753](typora图片/1595238643753.png)

**View**

  View是视图层， 也就是用户界面。前端主要由HTH L和csS来构建， 为了更方便地展现vi eu to del或者Hodel层的数据， 已经产生了各种各样的前后端模板语言， 比如FreeMarker，Thyme leaf等等， 各大MV VM框架如Vue.js.Angular JS， EJS等也都有自己用来构建用户界面的内置模板语言。

**Model**

  Model是指数据模型， 泛指后端进行的各种业务逻辑处理和数据操控， 主要围绕数据库系统展开。这里的难点主要在于需要和前端约定统一的接口规则

**ViewModel**

  ViewModel是由前端开发人员组织生成和维护的视图数据层。在这一层， 前端开发者对从后端获取的Model数据进行转换处理， 做二次封装， 以生成符合View层使用预期的视图数据模型。
  需要注意的是View Model所封装出来的数据模型包括视图的状态和行为两部分， 而Model层的数据模型是只包含状态的

- 比如页面的这一块展示什么，那一块展示什么这些都属于视图状态(展示)
- 页面加载进来时发生什么，点击这一块发生什么，这一块滚动时发生什么这些都属于视图行为(交互)

  视图状态和行为都封装在了View Model里。这样的封装使得View Model可以完整地去描述View层。由于实现了双向绑定， View Model的内容会实时展现在View层， 这是激动人心的， 因为前端开发者再也不必低效又麻烦地通过操纵DOM去更新视图。
  MVVM框架已经把最脏最累的一块做好了， 我们开发者只需要处理和维护View Model， 更新数据视图就会自动得到相应更新，真正实现`事件驱动编程`。
  View层展现的不是`Model`层的数据， 而是`ViewModel`的数据， 由`ViewModel`负责与`Model`层交互， 这就**完全解耦了View层和Model层， 这个解耦是至关重要的， 它是前后端分离方案实施的重要一环。**

# 5、Vue

Vue(读音/vju/， 类似于view) 是一套用于构建用户界面的渐进式框架， 发布于2014年2月。与其它大型框架不同的是， Vue被设计为可以自底向上逐层应用。Vue的核心库只关注视图层， 不仅易于上手， 还便于与第三方库(如：vue-router，vue-resource，vue x) 或既有项目整合。

## 1、MVVM模式的实现者

- Model：模型层， 在这里表示JavaScript对象
- View：视图层， 在这里表示DOM(HTML操作的元素)
- ViewModel：连接视图和数据的中间件， Vue.js就是MVVM中的View Model层的实现者

  在MVVM架构中， 是不允许数据和视图直接通信的， 只能通过ViewModel来通信， 而View Model就是定义了一个Observer观察者

- ViewModel能够观察到数据的变化， 并对视图对应的内容进行更新
- ViewModel能够监听到视图的变化， 并能够通知数据发生改变

  至此， 我们就明白了， Vue.js就是一个MV VM的实现者， 他的核心就是实现了DOM监听与数据绑定

## 2、为什么要使用Vue.js

- 轻量级， 体积小是一个重要指标。Vue.js压缩后有只有20多kb(Angular压缩后56kb+，React压缩后44kb+)
- 移动优先。更适合移动端， 比如移动端的Touch事件
- 易上手，学习曲线平稳，文档齐全
- 吸取了Angular(模块化) 和React(虚拟DOＭ) 的长处， 并拥有自己独特的功能，如：计算属性
- 开源，社区活跃度高
- ……

# 6、第一个Vue程序

   【说明】IDEA可以安装Vue的插件!
  注意：Vue不支持IE 8及以下版本， 因为Vue使用了IE 8无法模拟的ECMAScript 5特性。但它支持所有兼容ECMAScript 5的浏览器。

## 1、下载地址

- 开发版本
  - 包含完整的警告和调试模式：https：//yuejs.org/js/vue.js
  - 删除了警告， 30.96KBmin+gzip：https：//vuejs.org/js/vue.min.js
- CDN
  - `<script src=“https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js”></script>`
  - `<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>`

## 2、代码编写

  Vue.js的核心是实现了MVVM模式， 她扮演的角色就是View Model层， 那么所谓的第一个应用程序就是展示她的数据绑定功能，操作流程如下：

  1. **创建一个HTML文件**

     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <title>Title</title>
     </head>
     <body>
     
     </body>
     </html>
     
     ```

  2. **引入Vue.js**

     ```js
     <!--1.导入Vue.js-->
     <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
     
     ```

  3. **创建一个Vue实例**

     ```vue
     <script type="text/javascript">
         var vm = new Vue({
             el:"#app",
             /*Model：数据*/
             data:{
                 message:"hello,vue!"
             }
         });
     </script>
     
     ```

     说明：

     - `el: '#vue'`：绑定元素的ID
     - `data:{message:'Hello Vue!'}`：数据对象中有一个名为message的属性，并设置了初始值 Hello Vue！

  4. 将数据绑定到页面元素

     ```vue
     <!--view层，模板-->
     <div id="app">
         {{message}}
     </div>
     ```

     说明：只需要在绑定的元素中使用双花括号将Vue创建的名为message属性包裹起来， 即可实现数据绑定功能， 也就实现了View Model层所需的效果， 是不是和EL表达式非常像?

## 3、完整的HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

</head>
<body>

<!--view层，模板-->
<div id="app">
    {{message}}
</div>

<!--1.导入Vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        /*Model：数据*/
        data:{
            message:"hello,vue!"
        }
    });
</script>
</body>
</html>

```

## 4、测试

  为了能够更直观的体验Vue带来的数据绑定功能， 我们需要在浏览器测试一番， 操作流程如下：

1. 在浏览器上运行第一个Vue应用程序， 进入开发者工具

2. 在控制台输入vm.message=‘HelloWorld’， 然后回车， 你会发现浏览器中显示的内容会直接变成HelloWorld
3. 此时就可以在控制台直接输入vm.message来修改值， 中间是可以省略data的， 在这个操作中， 我并没有主动操作DOM， 就让页面的内容发生了变化， 这就是借助了Vue的数据绑定功能实现的； MV VM模式中要求View Model层就是使用观察者模式来实现数据的监听与绑定， 以做到数据与视图的快速响应。

## 5、v-bind

- 我们已经成功创建了第一个Vue应用!看起来这跟渲染一个字符串模板非常类似， 但是Vue在背后做了大量工作。现在数据和DOM已经被建立了关联， 所有东西都是响应式的。我们在控制台操作对象属性，界面可以实时更新!

- 我们还可以使用v-bind来绑定元素特性!

- **上代码**

  ```html
  <!DOCTYPE html>
  <html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  
  </head>
  <body>
  
  <!--view层，模板-->
  <div id="app">
      <span v-bind:title="message">
      鼠标悬停几秒钟查看此处动态绑定的提示信息！
    </span>
  </div>
  
  <!--1.导入Vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script type="text/javascript">
      var vm = new Vue({
          el:"#app",
          /*Model：数据*/
          data:{
              message: '页面加载于 ' + new Date().toLocaleString()
          }
      });
  </script>
  </body>
  </html>
  
  ```

- 你看到的v-bind等被称为指令。指令带有前缀v以表示它们是Vue提供的特殊特性。可能你已经猜到了， 它们会在渲染的DOM上应用特殊的响应式行为在这里，该指令的意思是：“将这个元素节点的title特性和Vue实例的message属性保持一致”。

- 如果你再次打开浏览器的JavaScript控制台， 输入app.message=‘新消息’，就会再一次看到这个绑定了title特性的HTML已经进行了更新。

## 6、v-if， v-else

什么是条件判断语句，就不需要我说明了吧，以下两个属性!

- `v-if`

- `v-else`

- **上代码**

  ```html
  <!DOCTYPE html>
  <html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <!--view层，模板-->
  <div id="app">
      <h1 v-if="ok">Yes</h1>
      <h1 v-else>No</h1>
  
  </div>
  
  <!--1.导入Vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script type="text/javascript">
      var vm = new Vue({
          el:"#app",
          /*Model：数据*/
          data:{
              ok: true
          }
      });
  </script>
  </body>
  </html>
  ```

测试：
1.在浏览器上运行，打开控制台!
2.在控制台输入`vm.ok=false`然后回车，你会发现浏览器中显示的内容会直接变成NO
  注：使用`v-*`属性绑定数据是不需要`双花括号`包裹的

## v-else-if

- v-if

- v-else-if

- v-else

- <font color=red>注：`===`三个等号在JS中表示绝对等于(就是数据与类型都要相等)上代码：</font>

  ```xml
  <!DOCTYPE html>
  <html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <!--view层，模板-->
  <div id="app">
      <h1 v-if="type==='A'">A</h1>
      <h1 v-else-if="type==='B'">B</h1>
      <h1 v-else-if="type==='D'">D</h1>
      <h1 v-else>C</h1>
  
  </div>
  
  <!--1.导入Vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script type="text/javascript">
      var vm = new Vue({
          el:"#app",
          /*Model：数据*/
          data:{
              type: 'A'
          }
      });
  </script>
  </body>
  </html>
  
  ```

## 3、v-for

- v-for

  ```html
  <div id="app">
      <li v-for="(item,index) in items">
          {{item.message}}---{{index}}
      </li>
  
  </div>
  
  ```

- 注：`items`是数组，`item`是数组元素迭代的别名。我们之后学习的Thymeleaf模板引擎的语法和这个十分的相似！

- 上代码：

  ```html
  // 第一种
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <!--view层，模板-->
  <div id="app">
      <li v-for="(item,index) in items">
          {{item.message}}---{{index}}
      </li>
  
  </div>
  
  <!--1.导入Vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script type="text/javascript">
      var vm = new Vue({
          el:"#app",
          /*Model：数据*/
          data:{
              items:[
                  {message:'狂神说Java'},
                  {message:'狂神说前端'},
                  {message:'狂神说运维'}
              ]
          }
      });
  </script>
  </body>
  </html>
  
  //第二种
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
     <h1 v-for ="item in items">
       {{item.message}}
     </h1>
  </div>
  <!--导入vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script>
    var  vm = new Vue({
      el:"#app",
      data: {
        items : [
          {message:"狂神1"},
          {message:"狂神二" }
        ]
      }
    });
  </script>
  </body>
  </html>
  ```

- 测试：在控制台输入`vm.items.push({message：'狂神说运维'})`，尝试追加一条数据，你会发现浏览器中显示的内容会增加一条`狂神说运维`.

- v-on监听事件

- emsp;事件有Vue的事件、和前端页面本身的一些事件!我们这里的`click`是vue的事件， 可以绑定到Vue中的`methods`中的方法事件!

- **上代码**：

  ```html
  <!DOCTYPE html>
  <html lang="en" xmlns:v-on="http://www.w3.org/1999/xhtml">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <button v-on:click="sayHi">点我</button>
  </div>
  
  <script src="../js/vue.js"></script>
  <script type="text/javascript">
      var vm = new Vue({
          el:"#app",
          data:{
              message:'Hello World'
          },
          methods:{
              sayHi:function(event){
                  //'this'在方法里面指向当前Vue实例
                  alert(this.message);
              }
          }
      });
  </script>
  </body>
  </html>
  ```

- **点击测试**
  Vue还有一些基本的使用方式， 大家有需要的可以再跟着官方文档看看， 因为这些基本的指令几乎我们都见过了，一通百通!掌握学习的方式!

## 4.v-model

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div id="app">
  请输入文本 : <input type="text" v-model="message"> {{message}}
</div>
<!--导入vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
  var vm = new Vue({
     el: '#app',/*这个是标签*/
     data: {
       message:"123"
     }
          }
  );
</script>
</body>
</html>
```

![image-20220906204511786](typora图片/image-20220906204511786.png)

# 7、什么是双向数据绑定

  Vue.js是一个MV VM框架， 即数据双向绑定， 即当数据发生变化的时候， 视图也就发生变化， 当视图发生变化的时候，数据也会跟着同步变化。这也算是Vue.js的精髓之处了。
  值得注意的是，我们所说的数据双向绑定，一定是对于UI控件来说的非UI控件不会涉及到数据双向绑定。单向数据绑定是使用状态管理工具的前提。如果我们使用vue x那么数据流也是单项的，这时就会和双向数据绑定有冲突。

## 1、为什么要实现数据的双向绑定

  在`Vue.js`中，如果使用`vuex`， 实际上数据还是单向的， 之所以说是数据双向绑定，这是用的UI控件来说， 对于我们处理表单， `Vue.js`的双向数据绑定用起来就特别舒服了。即两者并不互斥，在全局性数据流使用单项，方便跟踪；局部性数据流使用双向，简单易操作。

# 8、在表单中使用双向数据绑定

  你可以用`v-model`指令在表单、及元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇， 但`v-model`本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。
  注意：`v-model`会忽略所有表单元素的`value`、`checked`、`selected`特性的初始值而总是将`Vue`实例的数据作为数据来源。你应该通过`JavaScript`在组件的`data`选项中声明初始值!

## 1、单行文本

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div id="app">
    输入的文本：<input type="text" v-model="message" value="hello">{{message}}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            message:""
        }
    });
</script>
</body>
</html>

```

## 2、多行文本

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div id="app">
   多行文本：<textarea v-model="pan"></textarea>&nbsp;&nbsp;多行文本是：{{pan}}
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            message:"Hello hello!"
        }
    });
</script>
</body>
</html>


```

## 3、单复选框

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<div id="app">
    单复选框：
    <input type="checkbox" id="checkbox" v-model="checked">
    &nbsp;&nbsp;
    <label for="checkbox">{{checked}}</label>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            checked:false
        }
    });
</script>
</body>
</html>

```

## 4、多复选框

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<div id="app">
    多复选框：
    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
    &nbsp;&nbsp;
    <label for="jack">Jack</label>
    <input type="checkbox" id="join" value="Join" v-model="checkedNames">
    &nbsp;&nbsp;
    <label for="join">Jack</label>
    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
    &nbsp;&nbsp;
    <label for="mike">Mike</label>
    <span>选中的值：{{checkedNames}}</span>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            checkedNames:[]
        }
    });
</script>
</body>
</html>
```

## 5、单选按钮

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<div id="app">
    单选框按钮
    <input type="radio" id="one" value="One" v-model="picked">
    <label for="one">One</label>
    <input type="radio" id="two" value="Two" v-model="picked">
    <label for="two">Two</label>
    <span>选中的值：{{picked}}</span>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            picked:'Two'
        }
    });
</script>
</body>
</html>
```

## 6、下拉框

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div id="app">
<!--    性别：
    <input type="radio" name="sex" value="男" v-model="pan">男
    <input type="radio" name="sex" value="女" v-model="pan">女
    <p>选中了：{{pan}}</p>-->

    下拉框:
    <select v-model="pan">
        <option value="" disabled>---请选择---</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
        <option>D</option>
    </select>
    <span>value:{{pan}}</span>



</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
            pan:"A"
        }
    });
</script>
</body>
</html>
```

  注意：`v-model`表达式的初始值未能匹配任何选项，元系将被渲染为“未选中”状态。 在iOS中， 这会使用户无法选择第一个选项，因为这样的情况下，iOS不会触发`change`事件。因此，更推荐像上面这样提供一个值为空的禁用选项。

# 9、什么是组件

- 组件是可复用的`Vue`实例， 说白了就是一组可以重复使用的模板， 跟`JSTL`的自定义标签、`Thymeleal`的`th:fragment`等框架有着异曲同工之妙，通常一个应用会以一棵嵌套的组件树的形式来组织：

  ![1595251605760](typora图片/1595251605760.png)

- 例如，你可能会有页头、侧边栏、内容区等组件，每个组件又包含了其它的像导航链接、博文之类的组件。

## 1、第一个Vue组件

  注意：在实际开发中，我们并不会用以下方式开发组件，而是采用`vue-cli`创建，`vue`模板文件的方式开发，以下方法只是为了让大家理解什么是组件。
  **使用Vue.component()方法注册组件，格式如下：**

```html
<div id="app">
  <pan></pan>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    //先注册组件
    Vue.component("pan",{
        
        template:'<li>Hello</li>'

    });
    //再实例化Vue
    var vm = new Vue({
        el:"#app",
    });
</script>
```

  说明：

- `Vue.component()`：注册组件
- `pan`：自定义组件的名字
- `template`：组件的模板

## 2、使用`props`属性传递参数

  像上面那样用组件没有任何意义，所以我们是需要传递参数到组件的，此时就需要使用`props`属性了！
  **注意：默认规则下props属性里的值不能为大写；**

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

</head>
<body>

<div id="app">
    <!--组件，传递给组件中的值：props-->
    <cpn v-for="item in items" v-bind:itemChild="item"/>
</div>
<!--1.导入vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    // 定义一个vue组件component组件
    Vue.component("cpn",{
        props: ['itemChild'],
        template:  `<li>{{itemChild}}</li>`
    })
    var vm = new Vue({
        el: '#app',
        data: {
            items: ['Java','Linux','前端']
        }
    });
</script>
</body>
</html>
```

  **说明**：

- `v-for="item in items"`：遍历`Vue`实例中定义的名为`items`的数组，并创建同等数量的组件
- `v-bind:itemChild="item"`：将遍历的`item`项绑定到组件中`props`定义名为`item`属性上；= 号左边的`itemChild`为`props`定义的属性名，右边的为`item in items` 中遍历的item项的值

# 10、什么是Axios

  Axios是一个开源的可以用在浏览器端和`Node JS`的异步通信框架， 她的主要作用就是实现AJAX异步通信，其功能特点如下：

- 从浏览器中创建`XMLHttpRequests`
- 从node.js创建http请求
- 支持Promise API[JS中链式编程]
- 拦截请求和响应
- 转换请求数据和响应数据
- 取消请求
- 自动转换JSON数据
- 客户端支持防御XSRF(跨站请求伪造)

  GitHub：[https://github.com/axios/axios](https://github.com/axios/axios)
  中文文档：[http://www.axios-js.com/](http://www.axios-js.com/)

## 1、为什么要使用Axios

​         由于`Vue.js`是一个视图层框架并且作者(尤雨溪) 严格准守SoC(关注度分离原则)所以`Vue.js`并不包含AJAX的通信功能， 为了解决通信问题， 作者单独开发了一个名为`vue-resource`的插件， 不过在进入2.0版本以后停止了对该插件的维护并推荐了`Axios`框架。少用jQuery， 因为它操作Dom太频繁!

## 2、第一个Axios应用程序

  咱们开发的接口大部分都是采用JSON格式， 可以先在项目里模拟一段JSON数据， 数据内容如下：创建一个名为data.json的文件并填入上面的内容， 放在项目的根目录下

```json
{
  "name": "狂神说Java",
  "url": "https://blog.kuangstudy.com",
  "page": 1,
  "isNonProfit": true,
  "address": {
    "street": "含光门",
    "city": "陕西西安",
    "country": "中国"
  },
  "links": [
    {
      "name": "bilibili",
      "url": "https://space.bilibili.com/95256449"
    },
    {
      "name": "狂神说Java",
      "url": "https://blog.kuangstudy.com"
    },
    {
      "name": "百度",
      "url": "https://www.baidu.com/"
    }
  ]
}
```

**测试代码**

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-binf="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--v-cloak 解决闪烁问题-->
    <style>
        [v-cloak]{
            display: none;
        }
    </style>
</head>
<body>
<div id="vue"  v-cloak>
    <div>地名：{{info.name}}</div>
    <div>地址：{{info.address.country}}--{{info.address.city}}--{{info.address.street}}</div>
    <div>链接：<a v-bind:href="info.url" target="_blank">{{info.url}}</a> </div>
</div>

<!--引入js文件-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>

<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#vue",
        //data：属性：vm
        data(){
            return{
                info:{
                    name:null,
                    address:{
                        country:null,
                        city:null,
                        street:null
                    },
                    url:null
                }
            }
        },
        mounted(){//钩子函数
            axios
                .get('data.json')
                .then(response=>(this.info=response.data));
        }
    });
</script>


</body>
</html>
```

说明：

1. v-cloak解决页面闪烁问题（不会出现{{message}}这样的信息）
2. 在这里使用了v-bind将a:href的属性值与Vue实例中的数据进行绑定
3. 使用axios框架的get方法请求AJAX并自动将数据封装进了Vue实例的数据对象中
4. 我们在data中的数据结构必须和`Ajax`响应回来的数据格式匹配！

# 11、Vue的生命周期

  官方文档：https://cn.vuejs.org/v2/guide/instance.html#生命周期图示
  Vue实例有一个完整的生命周期，也就是从开始创建初女台化数据、编译模板、挂载DOM、渲染一更新一渲染、卸载等一系列过程，我们称这是Vue的生命周期。通俗说就是Vue实例从创建到销毁的过程，就是生命周期。
  在Vue的整个生命周期中，它提供了一系列的事件，可以让我们在事件触发时注册JS方法，可以让我们用自己注册的JS方法控制整个大局，在这些事件响应方法中的this直接指向的是Vue的实例。

![1595253373596](typora图片/1595253373596.png)

# 12、什么是计算属性

  计算属性的重点突出在`属性`两个字上(属性是名词)，首先它是个`属性`其次这个属性有`计算`的能力(计算是动词)，这里的`计算`就是个函数：简单点说，它就是一个能够将计算结果缓存起来的属性(将行为转化成了静态的属性)，仅此而已；可以想象为缓存!

**上代码**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!--view层，模板-->
<div id="app">
    <p>currentTime1:{{currentTime1()}}</p>
    <p>currentTime2:{{currentTime2}}</p>
</div>

<!--1.导入Vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    var vm = new Vue({
        el:"#app",
        data:{
          message:"message"
        },
        methods:{
            currentTime1:function(){
                return Date.now();//返回一个时间戳
            }
        },
        computed:{
            currentTime2:function(){//计算属性：methods，computed方法名不能重名，重名之后，只会调用methods的方法
                this.message;
                return Date.now();//返回一个时间戳
            }
        }
    });
</script>
</body>
</html>
```

  <font color=red>注意：methods和computed里的东西不能重名</font>
说明：

- methods：定义方法， 调用方法使用currentTime1()， 需要带括号
- computed：定义计算属性， 调用属性使用currentTime2， 不需要带括号：this.message是为了能够让currentTime2观察到数据变化而变化
- 如何在方法中的值发生了变化，则缓存就会刷新!可以在控制台使用`vm.message=”qinjiang"`， 改变下数据的值，再次测试观察效果

**结论：**
  调用方法时，每次都需要讲行计算，既然有计算过程则必定产生系统开销，那如果这个结果是不经常变化的呢?此时就可以考虑将这个结果缓存起来，采用计算属性可以很方便的做到这点，**计算属性的主要特性就是为了将不经常变化的计算结果进行缓存，以节约我们的系统开销；**

# 13、内容分发

  在`Vue.js`中我们使用`<slot>`元素作为承载分发内容的出口，作者称其为插槽，可以应用在组合组件的场景中；

## 测试

  比如准备制作一个待办事项组件(todo) ， 该组件由待办标题(todo-title) 和待办内容(todo-items)组成，但这三个组件又是相互独立的，该如何操作呢?

- **定义一个待办事项的组件**

```html
<div id="app">
    <todo></todo>
</div>
<!--1.导入Vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    Vue.component('todo',{
        template:'<div>\
                <div>代办事项</div>\
                <ul>\
                    <li>学习狂神说Java</li>\
                </ul>\
            </div>'
    })
</script>
```

- **我们需要让，代办事项的标题和值实现动态绑定，怎么做呢？我们可以留一个插槽！**

  1. 将上面的代码留出一个插槽，即slot

    ```html
  Vue.component('todo',{
  template:'<div>\
      <slot name="todo-title"></slot>\
      <ul>\
          <slot name="todo-items"></slot>\
      </ul>\
  </div>'
  });
  
    ```

  2. 定义一个名为todo-title的待办标题组件 和 todo-items的待办内容组件

    ```javascript
  Vue.component('todo-title',{
      props:['title'],
      template:'<div>{{title}}</div>'
  });
  
  //这里的index，就是数组的下标，使用for循环遍历的时候，可以循环出来！
  Vue.component("todo-items",{
      props:["item","index"],
      template:"<li>{{index+1}},{{item}}</li>"
  });
    ```

  3. 实例化Vue并初始化数据

    ```javascript
  var vm = new Vue({
      el:"#vue",
      data:{
          todoItems:['狂神说java','狂神说前端','狂神说运维']
      }
  });
    ```

  4. 将这些值，通过插槽插入

    ```html
  <div id="vue">
      <todo>
          <todo-title slot="todo-title" title="秦老师系列课程"></todo-title>
          <!--<todo-items slot="todo-items" v-for="{item,index} in todoItems" v-bind:item="item"></todo-items>-->
          <!--如下为简写-->
          <todo-items slot="todo-items" v-for="item in todoItems" :item="item"></todo-items>
      </todo>
  </div>
    ```

  说明：我们的todo-title和todo-items组件分别被分发到了todo组件的todo-title和todo-items插槽中
  
完整代码如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!--view层，模板-->
<div id="vue">
    <todo>
        <todo-title slot="todo-title" title="title"></todo-title>
        <!--<todo-items slot="todo-items" v-for="{item,index} in todoItems" v-bind:item="item"></todo-items>-->
        <!--如下为简写-->
        <todo-items slot="todo-items" v-for="item in todoItems" :item="item"></todo-items
    </todo>
</div>
<!--1.导入Vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    Vue.component('todo',{
        template:'<div>\
                <slot name="todo-title"></slot>\
                <ul>\
                    <slot name="todo-items"></slot>\
                </ul>\
            </div>'
    });
    Vue.component('todo-title',{
        props:['title'],
        template:'<div>{{title}}</div>'
    });
    //这里的index，就是数组的下标，使用for循环遍历的时候，可以循环出来！
    Vue.component("todo-items",{
        props:["item","index"],
        template:"<li>{{index+1}},{{item}}</li>"
    });

    var vm = new Vue({
        el:"#vue",
        data:{
            title:"秦老师系列课程",
            todoItems:['test1','test2','test3']
        }
    });
</script>
</body>
</html>
```

# 14、自定义事件

  通以上代码不难发现，数据项在Vue的实例中， 但删除操作要在组件中完成， 那么组件如何才能删除Vue实例中的数据呢?此时就涉及到参数传递与事件分发了， Vue为我们提供了自定义事件的功能很好的帮助我们解决了这个问题； 使用this.$emit(‘自定义事件名’， 参数) ， 操作过程如下：

    1. 在vue的实例中增加了methods对象并定义了一个名为removeTodoltems的方法

```js
var vm = new Vue({
    el: '#app',
    data: {
        title:"秦老师系列课程",
        todoItems:['狂神说java','狂神说前端','狂神说运维']
    },
    methods: {
        removeItems(index) {
            console.log("删除了" + this.todoItems[index] + "OK")
            this.todoItems.splice(index,1)//一次删除一个元素
        }
    }
});
```

    2. 修改todo-items待办内容组件的代码，增加一个删除按钮，并且绑定事件！

```js
//这里的index，就是数组的下标，使用for循环遍历的时候，可以循环出来！
Vue.component("todo-items",{
    props:["item",'index'],
    template:`<li>{{index}}——{{item}}<button @click="remove">删除</button></li>`,
    methods: {
        remove(index) {
            this.$emit('remove',index)
        }
    }
});
```

    3. 修改todo-items待办内容组件的HTML代码，增加一个自定义事件，比如叫remove，可以和组件的方法绑定，然后绑定到vue的方法！

```html
<!--增加了v-on:remove="removeTodoItems"自定义事件，该组件会调用Vue实例中定义的-->
<todo-items slot="todo-items" v-for="(item,index) in todoItems" 
			:index="index" :item="item" @remove="removeItems"></todo-items>
```

**对上一个代码进行修改，实现删除功能**

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<div id="app">
    <todo>
        {{title}}
        <todo-title slot="todo-title" :title="title"></todo-title>
        <!--<todo-items slot="todo-items" v-for="{item,index} in todoItems" 
						v-bind:item="item"></todo-items>-->
        <!--如下为简写-->
        <todo-items slot="todo-items" v-for="(item,index) in todoItems"
                    :index="index" :item="item" @remove="removeItems"></todo-items>
        <div>你好啊</div>
        <div>你好啊</div>
        <div>你好啊</div>
        <div slot="aaa">你好你好</div>
    </todo>
</div>

<!--1.导入Vue.js-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script type="text/javascript">
    // slot:插槽
    Vue.component('todo',{
        template:'  <div>\
                        <slot name="todo-title"></slot>\
                        <ul>\
                            <slot name="todo-items"></slot>\
                        </ul>\
                        \<h1><slot></slot></h1>\
                        \<h2><slot name="aaa"></slot></h2>\
                   </div>'
    });

    Vue.component('todo-title',{
        props:['title'],
        template:'<div>{{title}}</div>'
    });

    //这里的index，就是数组的下标，使用for循环遍历的时候，可以循环出来！
    Vue.component("todo-items",{
        props:["item",'index'],
        template:`<li>{{index}}——{{item}}<button @click="remove">删除</button></li>`,
        methods: {
            remove(index) {
                this.$emit('remove',index)
            }
        }
    });

    var vm = new Vue({
        el: '#app',
        data: {
            title:"秦老师系列课程",
            todoItems:['狂神说java','狂神说前端','狂神说运维']
        },
        methods: {
            removeItems(index) {
                console.log("删除了" + this.todoItems[index] + "OK")
                this.todoItems.splice(index,1)//一次删除一个元素
            }
        }
    });
</script>
</body>
</html>
```

## 逻辑理解

![1595295779847](typora图片/自定义事件.png)

# 15、Vue入门小结

核心：数据驱动，组件化

优点：借鉴了AngularJS的模块化开发和React的虚拟Dom，虚拟Dom就是把Demo操作放到内存中执行；

常用的属性：

- v-if
- v-else-if
- v-else
- v-for
- v-on绑定事件，简写@
- v-model数据双向绑定
- v-bind给巨剑绑定参数，简写：

组件化：

- 组合组件slot插槽
- 组件内部绑定事件需要使用到`this.$emit("事件名",参数);`
- 计算属性的特色，缓存计算数据

  遵循SoC关注度分离原则，Vue是纯粹的视图框架，并不包含，比如Ajax之类的通信功能，为了解决通信问题，我们需要使用Axios框架做异步通信；

## 说明

Vue的开发都是要基于NodeJS，实际开发采用Vue-cli脚手架开发，vue-router路由，vuex做状态管理；Vue UI，界面我们一般使用ElementUI（饿了么出品），或者ICE（阿里巴巴出品）来快速搭建前端项目~~

官网：

- https://element.eleme.cn/#/zh-CN

- https://ice.work/

  

# 一.黑马的Vue

![image-20220909002120658](typora图片/image-20220909002120658.png)

![image-20220909004254314](typora图片/image-20220909004254314.png)

![image-20220909004322814](typora图片/image-20220909004322814.png)

![image-20220909004719974](typora图片/image-20220909004719974.png)

![image-20220909005020503](typora图片/image-20220909005020503.png)

![image-20220909005603490](typora图片/image-20220909005603490.png)

![image-20220909010105013](typora图片/image-20220909010105013.png)

![image-20220909010302205](typora图片/image-20220909010302205.png)



# 二.黑马的Ajax

![image-20220909011233985](typora图片/image-20220909011233985.png)

![image-20220909011951401](typora图片/image-20220909011951401.png)

# 三.黑马的axios

![image-20220909012038849](typora图片/image-20220909012038849.png)

![image-20220909012320696](typora图片/image-20220909012320696.png)

# 四.Json

![image-20220909012534133](typora图片/image-20220909012534133.png)

![image-20220909012613115](typora图片/image-20220909012613115.png)

![image-20220909014532576](typora图片/image-20220909014532576.png)

![image-20220915185238661](typora图片/image-20220915185238661.png)