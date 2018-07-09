1.什么是vue生命周期 ?

vue实例从被创建到销毁的一系列过程就叫vue生命周期. 也就是从开始创建、初始化数据、编译模版、挂载DOM→渲染、更新、渲染、卸载等一系列过程。

2.axios的特点有哪些

axios是一个基于promise的HTTP库,支持promise的所有API
它可以拦截请求和响应
它可以转换请求数据和响应数据,并对响应回来的内容自动转换为json类型的数据
它安全性更高,客户端支持防御XSRF
3.vue父组件怎么给子组件传值?

父组件的数据要通过prop传到子组件

vue参考链接

4.请说下具体使用vue的理解

我也不知道题目到底问些什么（是问vue的具体使用过程还是问使用vue的优缺点呢？）

5.active-class是哪个组件的属性?嵌套路由怎么定义?

vue-router模块的router-link组件

  const routes = [
     { path: "/", redirect: "/home" },//重定向,指向了home组件
     {
         path: "/home", component: home,
        children: [
            { path: "/home/game", component: game }
         ]
    }
 ]

6.谈谈javascript数组排序方法sort()的使用,重点介绍参数使用及内部机制?

语法：arrayObject.sort(sortby)

参数sortby可选，规定排序顺序，必须是函数

注：如果调用该方法是没有使用参数，将按字符编码的顺序进行排序，要实现这一点，首先应把数组的元素都转换成字符串，以便进行比较。

如果想按照其他的标准进行排序，就需要两个比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对排序的数字。比较函数应该具有两个参数a和b，其返回值如下：

若a<b，则返回一个小于0的值

若a=b，则返回一个0

若a>b，则返回一个大于0的值

7.简述DIV元素和span元素的区别

div是一个块级元素，span是内嵌元素。块元素相当于内嵌元素在前后各加了一个换行。其实，块元素和行内元素也不是一成不变的，只要给块元素定义display：inline，块元素就变成了内嵌元素，同样的，给内嵌元素定义了display：block就变成了块元素了。

8.说几条XHTML规范的内容(至少3条)

所有的标记都必须有一个相应的结束标记
所有标签的元素和属性的名字都必须使用小写
所有的xml标记都必须合理嵌套
所有的属性值都必须用引号“”括起来
所有的<和&特殊符号用编码表示
给所有属性赋一个值
9.对web标准化(或网站重构)知道哪些相关的知识,简述几条你知道的Web标准?

网页主要有三部分组成：结构（Structrue）、表现（presentation）和行为（Behavior）。对应的网站标准也分为三方面：

结构化标准语言，主要包括XHTML和XML；
表现标准主要包括css
行为标准主要包括对象模型（如W3C  DOM）、ECMAScript等
10.localstorage和sessionstorage是什么?区别是什么?

localstorage和sessionstorage一样都是用来存储客户端临时信息的对象，他们均只能存储字符串类型对象

localstorage生命周期是永久的，这意味着除非用户在浏览器提供的UI上清除localstorage信息，否则这些信息将永远存在。

sessionstorage生命周期为当前窗口或标签，一旦窗口或标签被永久关闭了，那么所有通过sessionstorage存储的数据也将被清空。

不同浏览器无法共享localstorage或sessionstorage中的信息。相同浏览器的不同页面可以共享相同的localstorage（页面属于相同的域名和端口），但是不同页面或标签间无法共享sessionstorage。这里需要注意的是，页面及标签仅指顶级窗口，如果一个标签页包含多个iframe标签他们属于同源页面，那么他们之间是可以共享sessionstorage的。

11.如何获取一个元素的属性值

element.getAttribute('属性名称')

12.举例说明一下什么是事件委托?

事件委托就是利用冒泡的原理，把事件加到父元素或祖先元素上，触发执行效果

    <ul id="ul1">
        <li>111</li>
        <li>222</li>
        <li>333</li>
        <li>444</li>
    </ul>
    <script>
        window.onload = function () {
                var oUl = document.getElementById('ul1');
                oUl.onclick = function (ev) {
                        var ev = ev || window.event;
                        var target = ev.target || ev.srcElement;
                        if(target.nodeName.toLowerCase() == 'li') {
                                alert(target.innerHTML)
                        }
                }
        }
    </script>

13.json和jsonp的区别?

json返回的是一串json格式数据；而jsonp返回的是脚本代码（包含一个函数调用）

jsonp的全名叫做json with padding，就是把json对象用符合js语法的形式包裹起来以使其他的网站可以请求到，也就是将json封装成js文件传过去。



1.vue的虚拟dom？

虚拟的DOM的核心思想是：对复杂的文档DOM结构，提供一种方便的工具，进行最小化地DOM操作。

2.如何理解vue中MVVM模式？

MVVM全称是Model-View-ViewModel；vue是以数据为驱动的，一旦创建dom和数据就保持同步，每当数据发生变化时，dom也会变化。DOMListeners和DataBindings是实现双向绑定的关键。DOMListeners监听页面所有View层DOM元素的变化，当发生变化，Model层的数据随之变化；DataBindings监听Model层的数据，当数据发生变化，View层的DOM元素随之变化。

3.vue中<keep-alive>的作用？

把切换出去的组件保留在缓存中，可以保留组件的状态或者避免重新渲染。

4.vue生命周期的理解？



总共分为8个阶段：


beforeCreate----创建前 组件实例更被创建，组件属性计算之前，数据对象data都为undefined，未初始化。
created----创建后  组件实例创建完成，属性已经绑定，数据对象data已存在，但dom未生成，$el未存在
beforeMount---挂载前   vue实例的$el和data都已初始化，挂载之前为虚拟的dom节点，data.message未替换
mounted-----挂载后 vue实例挂载完成，data.message成功渲染。
beforeUpdate----更新前 当data变化时，会触发beforeUpdate方法
updated----更新后  当data变化时，会触发updated方法
beforeDestory---销毁前 组件销毁之前调用
destoryed---销毁后 组件销毁之后调用，对data的改变不会再触发周期函数，vue实例已解除事件监听和dom绑定，但dom结构依然存在

5.组件之间的传值通信？

  父组件向子组件传值：

    1）子组件在props中创建一个属性，用来接收父组件传过来的值；

    2）在父组件中注册子组件；

    3）在子组件标签中添加子组件props中创建的属性；

    4）把需要传给子组件的值赋给该属性

  子组件向父组件传值：

    1）子组件中需要以某种方式（如点击事件）的方法来触发一个自定义的事件；

    2）将需要传的值作为$emit的第二个参数，该值将作为实参传给响应事件的方法；

    3）在父组件中注册子组件并在子组件标签上绑定自定义事件的监听。



二. v-show和v-if指令的共同点和不同点?
v-show指令是通过修改元素的displayCSS属性让其显示或者隐藏
v-if指令是直接销毁和重建DOM达到让元素显示和隐藏的效果
三. 如何让CSS只在当前组件中起作用?
将当前组件的<style>修改为<style scoped>

四. <keep-alive></keep-alive>的作用是什么?
<keep-alive></keep-alive> 包裹动态组件时，会缓存不活动的组件实例,主要用于保留组件状态或避免重新渲染。

大白话: 比如有一个列表和一个详情，那么用户就会经常执行打开详情=>返回列表=>打开详情…这样的话列表和详情都是一个频率很高的页面，那么就可以对列表组件使用<keep-alive></keep-alive>进行缓存，这样用户每次返回列表的时候，都能从缓存中快速渲染，而不是重新渲染

五. Vue中引入组件的步骤?
1.采用ES6的import ... from ...语法或CommonJS的require()方法引入组件
2.对组件进行注册,代码如下

// 注册
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
3.使用组件<my-component></my-component>

六. 指令v-el的作用是什么?
提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标.可以是 CSS 选择器，也可以是一个 HTMLElement 实例,

七. 在Vue中使用插件的步骤
采用ES6的import ... from ...语法或CommonJSd的require()方法引入插件
使用全局方法Vue.use( plugin )使用插件,可以传入一个选项对象Vue.use(MyPlugin, { someOption: true })
八. 请列举出3个Vue中常用的生命周期钩子函数?
created: 实例已经创建完成之后调用,在这一步,实例已经完成数据观测, 属性和方法的运算, watch/event事件回调. 然而, 挂载阶段还没有开始, $el属性目前还不可见
mounted: el被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。如果 root 实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内。
activated::keep-alive组件激活时调用
九. 请简述下Vuex的原理和使用方法
数据单向流动
数据单向流动
一个应用可以看作是由上面三部分组成: View, Actions,State,数据的流动也是从View => Actions => State =>View 以此达到数据的单向流动.但是项目较大的, 组件嵌套过多的时候, 多组件共享同一个State会在数据传递时出现很多问题.Vuex就是为了解决这些问题而产生的.

Vuex可以被看作项目中所有组件的数据中心,我们将所有组件中共享的State抽离出来,任何组件都可以访问和操作我们的数据中心.

Vuex原理
上图可以很好的说明Vuex的组成,一个实例化的Vuex.Store由state, mutations和actions三个属性组成:

state中保存着共有数据
改变state中的数据有且只有通过mutations中的方法,且mutations中的方法必须是同步的
如果要写异步的方法,需要些在actions中, 并通过commit到mutations中进行state中数据的更改.
更多Vuex信息,请参考Vuex官网 : vuex.vuejs.org

十. 请谈谈Vue框架和Angular.js和React的不同
参见:Vue对比其他框架


作者：Lee_tanghui
链接：https://www.jianshu.com/p/e54a9a34a773
來源：简书



2、下列面试题

active-class是哪个组件的属性？
vue-router模块的router-link组件。

嵌套路由怎么定义？
在实际项目中我们会碰到多层嵌套的组件组合而成，但是我们如何实现嵌套路由呢？因此我们需要在 VueRouter 的参数中使用 children 配置，这样就可以很好的实现路由嵌套。
index.html，只有一个路由出口

<div id="app">
    <!-- router-view 路由出口, 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
</div>
main.js，路由的重定向，就会在页面一加载的时候，就会将home组件显示出来，因为重定向指向了home组件，redirect的指向与path的必须一致。children里面是子路由，当然子路由里面还可以继续嵌套子路由。

import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)

//引入两个组件

import home from "./home.vue"
import game from "./game.vue"
//定义路由
const routes = [
    { path: "/", redirect: "/home" },//重定向,指向了home组件
    {
        path: "/home", component: home,
        children: [
            { path: "/home/game", component: game }
        ]
    }
]
//创建路由实例
const router = new VueRouter({routes})

new Vue({
    el: '#app',
    data: {
    },
    methods: {
    },
    router
})
home.vue，点击显示就会将子路由显示在出来，子路由的出口必须在父路由里面，否则子路由无法显示。

<template>
    <div>
        <h3>首页</h3>
        <router-link to="/home/game">
            <button>显示<tton>
        </router-link>
        <router-view></router-view>
    </div>
</template>
game.vue

 <template>
    <h3>游戏</h3>
</template>
怎么定义vue-router的动态路由？怎么获取传过来的动态参数？
在router目录下的index.js文件中，对path属性加上/:id。
使用router对象的params.id。

vue-router有哪几种导航钩子？
三种，
第一种：是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
第二种：组件内的钩子
第三种：单独路由独享组件

scss是什么？在vue.cli中的安装使用步骤是？有哪几大特性？
css的预编译。

使用步骤：

第一步：用npm 下三个loader（sass-loader、css-loader、node-sass）

第二步：在build目录找到webpack.base.config.js，在那个extends属性中加一个拓展.scss

第三步：还是在同一个文件，配置一个module属性

第四步：然后在组件的style标签加上lang属性 ，例如：lang=”scss”

有哪几大特性:

1、可以用变量，例如（$变量名称=值）；
2、可以用混合器，例如（）
3、可以嵌套

mint-ui是什么？怎么使用？说出至少三个组件使用方法？
基于vue的前端组件库。npm安装，然后import样式和js，vue.use（mintUi）全局引入。在单个组件局部引入：import {Toast} from ‘mint-ui’。
组件一：Toast(‘登录成功’)；
组件二：mint-header；
组件三：mint-swiper

v-model是什么？怎么使用？ vue中标签怎么绑定事件？
可以实现双向绑定，指令（v-class、v-for、v-if、v-show、v-on）。vue的model层的data属性。绑定事件：<input @click=doLog()/>

iframe的优缺点？
iframe也称作嵌入式框架，嵌入式框架和框架网页类似，它可以把一个网页的框架和内容嵌入在现有的网页中。

优点：

解决加载缓慢的第三方内容如图标和广告等的加载问题
Security sandbox
并行加载脚本
方便制作导航栏
缺点：

iframe会阻塞主页面的Onload事件
即时内容为空，加载也需要时间
没有语意
简述一下Sass、Less，且说明区别？
他们是动态的样式语言，是CSS预处理器,CSS上的一种抽象层。他们是一种特殊的语法/语言而编译成CSS。
变量符不一样，less是@，而Sass是$;
Sass支持条件语句，可以使用if{}else{},for{}循环等等。而Less不支持;
Sass是基于Ruby的，是在服务端处理的，而Less是需要引入less.js来处理Less代码输出Css到浏览器

axios是什么？怎么使用？描述使用它实现登录功能的流程？
请求后台资源的模块。npm install axios -S装好，然后发送的是跨域，需在配置文件中config/index.js进行设置。后台如果是Tp5则定义一个资源路由。js中使用import进来，然后.get或.post。返回在.then函数中如果成功，失败则是在.catch函数中

axios+tp5进阶中，调用axios.post(‘api/user’)是进行的什么操作？axios.put(‘api/user/8′)呢？
跨域，添加用户操作，更新操作。

vuex是什么？怎么使用？哪种功能场景使用它？
vue框架中状态管理。在main.js引入store，注入。新建了一个目录store，….. export 。场景有：单页应用中，组件之间的状态。音乐播放、登录状态、加入购物车

mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？
一个model+view+viewModel框架，数据模型model，viewModel连接两个

区别：vue数据驱动，通过数据来显示视图层而不是节点操作。

场景：数据操作比较多的场景，更加便捷

自定义指令（v-check、v-focus）的方法有哪些？它有哪些钩子函数？还有哪些钩子函数参数？
全局定义指令：在vue对象的directive方法里面有两个参数，一个是指令名称，另外一个是函数。组件内定义指令：directives

钩子函数：bind（绑定事件触发）、inserted(节点插入的时候触发)、update（组件内相关更新）

钩子函数参数：el、binding

说出至少4种vue当中的指令和它的用法？
v-if：判断是否隐藏；v-for：数据循环出来；v-bind:class：绑定一个属性；v-model：实现双向绑定

vue-router是什么？它有哪些组件？
vue用来写路由一个插件。router-link、router-view

导航钩子有哪些？它们有哪些参数？
导航钩子有：

a/全局钩子和组件内独享的钩子。b/beforeRouteEnter、afterEnter、beforeRouterUpdate、beforeRouteLeave

参数：

有to（去的那个路由）、from（离开的路由）、next（一定要用这个函数才能去到下一个路由，如果不用就拦截）最常用就这几种

Vue的双向数据绑定原理是什么？
vue.js 是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

具体步骤：

第一步：需要observe的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter和getter
这样的话，给这个对象的某个值赋值，就会触发setter，那么就能监听到了数据变化

第二步：compile解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图

第三步：Watcher订阅者是Observer和Compile之间通信的桥梁，主要做的事情是:
1、在自身实例化时往属性订阅器(dep)里面添加自己
2、自身必须有一个update()方法
3、待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退。

第四步：MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果。

请详细说下你对vue生命周期的理解？
总共分为8个阶段创建前/后，载入前/后，更新前/后，销毁前/后

创建前/后： 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，$el还没有。

载入前/后：在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换。在mounted阶段，vue实例挂载完成，data.message成功渲染。

更新前/后：当data变化时，会触发beforeUpdate和updated方法。

销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在
请说下封装 vue 组件的过程？
首先，组件可以提升整个项目的开发效率。能够把页面抽象成多个相对独立的模块，解决了我们传统项目开发：效率低、难维护、复用性等问题。

然后，使用Vue.extend方法创建一个组件，然后使用Vue.component方法注册组件。子组件需要数据，可以在props中接受定义。而子组件修改好数据后，想把数据传递给父组件。可以采用emit方法。

你是怎么认识vuex的？
vuex可以理解为一种开发模式或框架。比如PHP有thinkphp，java有spring等。
通过状态（数据源）集中管理驱动组件的变化（好比spring的IOC容器对bean进行集中管理）。

应用级的状态集中放在store中； 改变状态的方式是提交mutations，这是个同步的事物； 异步逻辑应该封装在action中。

vue-loader是什么？使用它的用途有哪些？
解析.vue文件的一个加载器，跟template/js/style转换成js模块。

用途：js可以写es6、style样式可以scss或less、template可以加jade等

请说出vue.cli项目中src目录每个文件夹和文件的用法？
assets文件夹是放静态资源；components是放组件；router是定义路由相关的配置;view视图；app.vue是一个应用主组件；main.js是入口文件

vue.cli中怎样使用自定义的组件？有遇到过哪些问题吗？
第一步：在components目录新建你的组件文件（smithButton.vue），script一定要export default {

第二步：在需要用的页面（组件）中导入：import smithButton from ‘../components/smithButton.vue’

第三步：注入到vue的子组件的components属性上面,components:{smithButton}

第四步：在template视图view中使用，<smith-button> </smith-button>
问题有：smithButton命名，使用的时候则smith-button。

聊聊你对Vue.js的template编译的理解？
简而言之，就是先转化成AST树，再得到的render函数返回VNode（Vue的虚拟DOM节点）

详情步骤：

首先，通过compile编译器把template编译成AST语法树（abstract syntax tree 即 源代码的抽象语法结构的树状表现形式），compile是createCompiler的返回值，createCompiler是用以创建编译器的。另外compile还负责合并option。

然后，AST会经过generate（将AST语法树转化成render funtion字符串的过程）得到render函数，render的返回值是VNode，VNode是Vue的虚拟DOM节点，里面有（标签名、子节点、文本等等）

vue的历史记录
history 记录中向前或者后退多少步

vuejs与angularjs以及react的区别？
1.与AngularJS的区别
相同点：

都支持指令：内置指令和自定义指令。

都支持过滤器：内置过滤器和自定义过滤器。

都支持双向数据绑定。

都不支持低端浏览器。

不同点：

1.AngularJS的学习成本高，比如增加了Dependency Injection特性，而Vue.js本身提供的API都比较简单、直观。

2.在性能上，AngularJS依赖对数据做脏检查，所以Watcher越多越慢。

Vue.js使用基于依赖追踪的观察并且使用异步队列更新。所有的数据都是独立触发的。

对于庞大的应用来说，这个优化差异还是比较明显的。

2.与React的区别
相同点：

React采用特殊的JSX语法，Vue.js在组件开发中也推崇编写.vue特殊文件格式，对文件内容都有一些约定，两者都需要编译后使用。

中心思想相同：一切都是组件，组件实例之间可以嵌套。

都提供合理的钩子函数，可以让开发者定制化地去处理需求。

都不内置列数AJAX，Route等功能到核心包，而是以插件的方式加载。

在组件开发中都支持mixins的特性。

不同点：

React依赖Virtual DOM,而Vue.js使用的是DOM模板。React采用的Virtual DOM会对渲染出来的结果做脏检查。

Vue.js在模板中提供了指令，过滤器等，可以非常方便，快捷地操作DOM。





vue生命周期面试题
什么是vue生命周期？
Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。

vue生命周期的作用是什么？
它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。

vue生命周期总共有几个阶段？
它可以总共分为8个阶段：创建前/后, 载入前/后,更新前/后,销毁前/销毁后

第一次页面加载会触发哪几个钩子？
第一次页面加载时会触发 beforeCreate, created, beforeMount, mounted 这几个钩子

DOM 渲染在 哪个周期中就已经完成？
DOM 渲染在 mounted 中就已经完成了

简单描述每个周期具体适合哪些场景？
生命周期钩子的一些使用方法： beforecreate : 可以在这加个loading事件，在加载实例时触发 created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用 mounted : 挂载元素，获取到DOM节点 updated : 如果对数据统一处理，在这里写上相应函数 beforeDestroy : 可以做一个确认停止事件的确认框 nextTick : 更新数据后立即操作dom

arguments是一个伪数组，没有遍历接口，不能遍历

cancas和SVG的是什么以及区别
SVG

SVG 是一种使用 XML 描述 2D 图形的语言。
SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。
在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。

Canvas

Canvas 通过 JavaScript 来绘制 2D 图形。
Canvas 是逐像素进行渲染的。
在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

Canvas 与 SVG 的比较

Canvas

依赖分辨率
不支持事件处理器
弱的文本渲染能力
能够以 .png 或 .jpg 格式保存结果图像
最适合图像密集型的游戏，其中的许多对象会被频繁重绘
SVG

不依赖分辨率
支持事件处理器
最适合带有大型渲染区域的应用程序（比如谷歌地图）
复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
不适合游戏应用

七、vue如何实现按需加载配合webpack设置
webpack中提供了require.ensure()来实现按需加载。以前引入路由是通过import 这样的方式引入，改为const定义的方式进行引入。
不进行页面按需加载引入方式：import home from '../../common/home.vue'
进行页面按需加载的引入方式：const home = r => require.ensure( [], () => r (require('../../common/home.vue')))



十九、生命周期相关面试题
总共分为8个阶段创建前/后，载入前/后，更新前/后，销毁前/后。

创建前/后： 在beforeCreate阶段，vue实例的挂载元素el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，el还没有。
载入前/后：在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换。在mounted阶段，vue实例挂载完成，data.message成功渲染。
更新前/后：当data变化时，会触发beforeUpdate和updated方法。
销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在
（1）、什么是vue生命周期
答： Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。

（2）、vue生命周期的作用是什么
答：它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。

（3）、vue生命周期总共有几个阶段
答：可以总共分为8个阶段：创建前/后, 载入前/后,更新前/后,销毁前/销毁后

（4）、第一次页面加载会触发哪几个钩子
答：第一次页面加载时会触发 beforeCreate, created, beforeMount, mounted 这几个钩子

（5）、DOM 渲染在 哪个周期中就已经完成
答：DOM 渲染在 mounted 中就已经完成了。

（6）、简单描述每个周期具体适合哪些场景
答：生命周期钩子的一些使用方法：

beforecreate : 可以在这加个loading事件，在加载实例时触发
created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用
mounted : 挂载元素，获取到DOM节点
updated : 如果对数据统一处理，在这里写上相应函数
beforeDestroy : 可以做一个确认停止事件的确认框
nextTick : 更新数据后立即操作dom
二十、说出至少4种vue当中的指令和它的用法？
v-if：判断是否隐藏；v-for：数据循环；v-bind:class：绑定一个属性；v-model：实现双向绑定

二十一、vue-loader是什么？使用它的用途有哪些？
解析.vue文件的一个加载器。
用途：js可以写es6、style样式可以scss或less、template可以加jade等

二十二、scss是什么？在vue.cli中的安装使用步骤是？有哪几大特性？
答：css的预编译。
使用步骤：
第一步：先装css-loader、node-loader、sass-loader等加载器模块
第二步：在build目录找到webpack.base.config.js，在那个extends属性中加一个拓展.scss
第三步：在同一个文件，配置一个module属性
第四步：然后在组件的style标签加上lang属性 ，例如：lang=”scss”

特性:

可以用变量，例如（$变量名称=值）；
可以用混合器，例如（）
可以嵌套
二十三、为什么使用key？
当有相同标签名的元素切换时，需要通过 key 特性设置唯一的值来标记以让 Vue 区分它们，否则 Vue 为了效率只会替换相同标签内部的内容。

二十四、为什么避免 v-if 和 v-for 用在一起
当 Vue 处理指令时，v-for 比 v-if 具有更高的优先级，通过v-if 移动到容器元素，不会再重复遍历列表中的每个值。取而代之的是，我们只检查它一次，且不会在 v-if 为否的时候运算 v-for。

二十五、VNode是什么？虚拟 DOM是什么？
Vue在 页面上渲染的节点，及其子节点称为“虚拟节点 (Virtual Node)”，简写为“VNode”。“虚拟 DOM”是由 Vue 组件树建立起来的整个 VNode 树的称呼。







开放性题目：
1、你在现在的团队处于什么样的角色，起到了什么明显的作用？
2、说说前端最近流行些什么，在自己以前的项目中都有应用哪些？常去哪些网站？

技术型题目：
1、请写出目前有哪些主流浏览器及对应的内核是叫什么？
1、IE浏览器内核：Trident内核，也被称为IE内核；
2、Chrome浏览器内核：Chromium内核 → Webkit内核 → Blink内核；
3、Firefox浏览器内核：Gecko内核，也被称Firefox内核；
4、Safari浏览器内核：Webkit内核；
5、Opera浏览器内核：最初是自主研发的Presto内核，后跟随谷歌，从Webkit到Blink内核；
6、360浏览器、猎豹浏览器内核：IE+Chrome双内核；
7、搜狗、遨游、QQ浏览器内核：Trident（兼容模式）+Webkit（高速模式）；
8、百度浏览器、世界之窗内核：IE内核；

2、请解释下JavaScript的同源策略？
同源策略简单的说就是一段脚本只能读取来自于同一来源的窗口和文档的属性，这里的同一来源指的是主机名、协议和端口号的组合。

3、什么是跨域，跨域请求资源的方法有哪些，你是如何解决跨域的？
参考博客：https://www.cnblogs.com/minigrasshopper/p/8573519.html
由于浏览器同源策略，凡是发送请求url的协议、域名、端口三者之间任意一与当前页面地址不同即为跨域。存在跨域的情况：
网络协议不同，如http协议访问https协议。
端口不同，如80端口访问8080端口。
域名不同，如qianduanblog.com访问baidu.com。
子域名不同，如abc.qianduanblog.com访问def.qianduanblog.com。
域名和域名对应ip,如www.a.com访问20.205.28.90.

2、跨域请求资源的方法：
(1)、porxy代理
定义和用法：proxy代理用于将请求发送给后台服务器，通过服务器来发送请求，然后将请求的结果传递给前端。

实现方法：通过nginx代理；

注意点：1、如果你代理的是https协议的请求，那么你的proxy首先需要信任该证书（尤其是自定义证书）或者忽略证书检查，否则你的请求无法成功。

(2)、CORS 【Cross-Origin Resource Sharing】

定义和用法：是现代浏览器支持跨域资源请求的一种最常用的方式。

使用方法：一般需要后端人员在处理请求数据的时候，添加允许跨域的相关操作。如下：

res.writeHead(200, {
    "Content-Type": "text/html; charset=UTF-8",
    "Access-Control-Allow-Origin":'http://localhost',
    'Access-Control-Allow-Methods': 'GET, POST, OPTIONS',
    'Access-Control-Allow-Headers': 'X-Requested-With, Content-Type'
});
1
2
3
4
5
6
(3)、jsonp

定义和用法：通过动态插入一个script标签。浏览器对script的资源引用没有同源限制，同时资源加载到页面后会立即执行（没有阻塞的情况下）。

特点：通过情况下，通过动态创建script来读取他域的动态资源，获取的数据一般为json格式。

实例如下：

html：

//原生js
<html>
<head>
    <title></title>
    <script type="text/javascript">

    var returnjs = function(data){
        alert(data.code);
    };
    // 提供jsonp服务的url地址（不管是什么类型的地址，最终生成的返回值都是一段javascript代码）
    var url = "http://www.return.com/jsonp/get?code=1&callback=returnjs";//数据接收后台
    // 创建script标签，设置其属性
    var script = document.createElement('script');
    script.setAttribute('src', url);
    // 把script标签加入head，此时调用开始
    document.getElementsByTagName('head')[0].appendChild(script);
    </script>
</head>
<body>
</body>
</html>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
//jQ版
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here1</title>
<script type="text/javascript" src="jq.js"></script><!-- 记得引入jq -->
</head>
<body>
<script type="text/javascript">
    jQuery(document).ready(function(){
       $.ajax({
            type: "get",
            async: false,
            url: "http://www.return.com/jsonp/get?code=1",//数据接收后台
            dataType: "jsonp",
            jsonp: "callback",//传递给请求处理程序或页面的，用以获得jsonp回调函数名的参数名(一般默认为:callback)
            jsonpCallback:"returnjs",//自定义的jsonp回调函数名称，默认为jQuery自动生成的随机函数名，也可以写"?"，jQuery会自动为你处理数据
            crossDomain:true,
            success: function(json){
                alert(json.code);
            },
            error: function(){
                alert('fail');
            }
        });
    });
</script>
</body>
</html>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
缺点：
　　1、这种方式无法发送post请求（这里）
　　2、另外要确定jsonp的请求是否失败并不容易，大多数框架的实现都是结合超时时间来判定。

4、请说说get和post请求的区别，什么时候用post？
1、GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符，安全性很低
2、POST：一般用于修改服务器上的资源，通过提交表单来传值，对所发送的信息没有限制，安全性比GET高
3、在以下情况中，使用 POST 请求：
无法使用缓存文件（更新服务器上的文件或数据库）
向服务器发送大量数据（POST 没有数据量限制）
发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠
需要修改服务器上的资源的时候

5、你有哪些性能优化的方法？
1. 减少 HTTP 请求
2. 减少 DNS 查找
3. 避免重定向
4. 使用 Ajax 缓存
5. 延迟载入组件
6. 预先载入组件
7. 减少 DOM 元素数量
8. 切分组件到多个域
9. 最小化 iframe 的数量
10. 不要出现http 404 错误

6、请写出函数运行结果。

function test(){
    var a;
    function foo(){
        return 2;
    }
    console.log(a);//undefined
    console.log(foo());//2
    a = 1;
}
test();
1
2
3
4
5
6
7
8
9
10
7、下面程序的结果。

function fun(n,o){
    console.log(o);
    return {
        fun:function(m){
            return fun(m,n);
        }
    }
}
var a = fun(0);a.fun(1);a.fun(2);a.fun(3);
var b = fun(0).fun(1).fun(2).fun(3);
var c = fun(0).fun(1);c.fun(2);c.fun(3);
//undefined 0 0 0
//undefined 0 1 2
//undefined 0 1 1
1
2
3
4
5
6
7
8
9
10
11
12
13
14
8、下面输出的结果。

var a = 9;
var b = a++ + a-- + ++a + --a + a--
//console.log(a);//8
//console.log(b);//47
1
2
3
4
9、什么是盒子模型？
https://blog.csdn.net/icessunt/article/details/60469260
一般来说，css盒子模型有两种模式：

W3C的标准模型 相当于 box-sizing：content-box
我们对元素设置的宽度和高度就是内容（content）的宽度和高度，也就是内盒子的宽度；外盒子的宽度包括：content+padding+border的。

当我们设置好了宽度和高度的时候，其外盒子的宽度和高度基本上就定了，当我们想在内容（content）外面设置padding和margin或者border时，非常容易破坏我们的布局，此时我们就需要想到box-sizing：border-box

IE的传统模型 相当于box-sizing：border-box
这个模型下，我们设置的宽度和高度是包括：content+padding+border的，但是不包括margin。其内容的宽度比我们设置的宽度要小的。

如果计算的content的内容宽度为负值，其都会被计算为0，内容还在，故不能通过border-box来隐藏元素。元素的内容宽度和高度是在我们设置的宽度和高度的里面渲染的。当我们想给元素添加border或者padding时，这个模型不会破坏我们的布局，因为其会适当的调整我们内容content的宽度和高度来满足。故可以用来设置自适应布局

10、let，const，var 区别？
var：函数作用域，存在变量提升
let：块作用域，不存在变量提升
const：不能修改的是栈内存在的值和地址。声明一个基本类型的时候为常量，不可修改；声明对象可以修改

11、以下代码显示结果为

var objName = "name1";
function obj(){
    var objName = "name2";
    function innerObj(){
        alert(objName);//name2
    }
    innerObj();
}
console.log(obj());//undefined
1
2
3
4
5
6
7
8
9
12、求数组最大值
1、sort排序（先把数组从小到大排序，数组第一个即为最小值，最后一个即为最大值）

ary.sort(function(a,b){return a-b;});
var minN = ary[0];
var maxN = ary[ary.length-1];
1
2
3
2、假设数组第一个为最大（或最小值），和后边进行比较，若后边的值比最大值大（或比最小值小），则替换最大值（或最小值）

var maxN = ary[0];
var minN = ary[0];
for(var i=1;i<ary.length;i++){
    var cur = ary[i];
    cur>maxN ? maxN=cur : null;
    cur<minN ? minN=cur : null;
}
1
2
3
4
5
6
7
3、Math的max和min方法

Math.max.apply(null, a);
Math.min.apply(null, a);
1
2
call()方法和apply()方法用法总结：https://blog.csdn.net/ganyingxie123456/article/details/70855586

13、编写一个方法 去掉一个数组的重复元素
方法一：

var arr = [0,2,3,4,4,0,2];
var obj = {};
var tmp = [];
for(var i = 0 ;i< arr.length;i++){
   if( !obj[arr[i]] ){
      obj[arr[i]] = 1;
      tmp.push(arr[i]);
   }
}
console.log(tmp);
1
2
3
4
5
6
7
8
9
10
结果如下： [0, 2, 3, 4]

方法二：

var arr = [2,3,4,4,5,2,3,6],
   arr2 = [];
for(var i = 0;i< arr.length;i++){
    if(arr2.indexOf(arr[i]) < 0){
        arr2.push(arr[i]);
    }
}
console.log(arr2);
1
2
3
4
5
6
7
8
结果为：[2, 3, 4, 5, 6]

方法三：

var arr = [2,3,4,4,5,2,3,6];
var arr2 = arr.filter(function(element,index,self){
    return self.indexOf(element) === index;
});
console.log(arr2);
1
2
3
4
5
结果为：[2, 3, 4, 5, 6]

方法三中用到的函数说明：

filter方法用于过滤数组成员，满足条件的成员组成一个新数组返回。
它的参数是一个函数，所有数组成员依次执行该函数，返回结果为true的成员组成一个新数组返回。该方法不会改变原数组。

filter方法的参数函数可以接受三个参数：当前成员，当前位置和整个数组。

indexOf方法返回给定元素在数组中第一次出现的位置，如果没有出现则返回-1。

13、用css实现垂直居中
https://www.cnblogs.com/zhouhuan/p/vertical_center.html

14、用es6的方法将数组[5,6,7]插入数组[1,2,3,4]，得到数组[1,2,5,6,7,3,4]。

var arry1 = [1,2,3,4];
var arry2 = [5,6,7];
//这里的...为扩展运算符（spread）：表示将一个数组转为用逗号分隔的参数序列。
arry1.splice(2,0,...arry2);
console.log(arry1);
1
2
3
4
5
splice方法用于删除原数组的一部分成员，并可以在删除的位置添加新的数组成员，返回值是被删除的元素。该方法会改变原数组。
splice方法的第一个参数是删除的起始位置（从0开始），第二个参数是被删除的元素个数（第二个参数设为0的时候表示只插入元素）。如果后面还有更多的参数，则表示这些就是要被插入数组的新元素。
…扩展运算符（spread）：将一个数组转为用逗号分隔的参数序列。