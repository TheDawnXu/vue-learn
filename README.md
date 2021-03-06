# VUE笔记

## VUE简介  
* [VUE简介](https://blog.csdn.net/liang377122210/article/details/71545459)
* 声明式渲染：简化数据的渲染方式，提供指令和双向绑定机制
* 组件化应用构建：提高HTML的独立性和可复用性


## VUE基本语法介绍

### 数据双向绑定 demo1

* 定义vue实例   
    new Vue({...})
* v-model 和 {{ ... }} 的数据绑定   
    在控制台输入 app.name = 'yyy' 页面同步更新
* v-model 和 {{...}}的内容说明   
    在他们的内容中支持简单的js表达式，比如：三目，js命令（typeof）
    ，但是不支持完整的js代码，比如：if(...){...}


### v-for 循环指令的使用 demo2

* 指令
* 遍历集合
* 在{{ ... }} 中解析json
* 在控制台添加数据 app.stu.push({name:'xiaoli', age: 15})

### v-bind 指令的使用 demo3

* 属性绑定
* 缩写的语法

### v-on 定义事件 demo4

* 基本使用
* 批量定义
* vue对象的methods属性
* 缩写

### v-model 与value的绑定 demo5

* 使用范围：input select textarea
* 修饰符：v-model.XXX (number转换为数字 trim去掉两边的控制 lazy延迟更新)

### v-if 和 v-show demo6

* 控制元素是否渲染/显示
* v-if和v-show的区别
* 可以和v-for连用

### 计算属性 computed demo7

* 作用：通过已有的属性计算新的属性
* 为什么不用表达式计算   
    可以直接在{{...}}中写表达式，但是使用表达式的方式就不能再
    vue对象中获取改属性的值，所以建议使用计算属性

### 组件 demo8 组建属性 demo9

* 定义组件 全局组件和局部组件   
    Vue.component({...})  
    new Vue({components: [{...}, {...}]})
* 为什么使用组件  
    1.简化主页面html代码的内容，2.提高html代码的可用性
* 组件中使用data   
    组件中的data必须是function，否则报错
* 组件的属性定义
    props:['a','b']，可以在组件的标签上使用，实现动态效果

### *组件通信 demo10

* 使用中间件实现组件同行
    定义一个vue实例来作为通信的中间件
* $on的介绍   
    实例的$XXX可以获取实例的内容，包含数据，方法，生命周期
    $on用来绑定事件，$.emit用来触发事件

### 过滤器 demo11

* 定义过滤器   
    Vue.filter('/*过滤器名称*/', function (val, pre) {});
    val表示要过滤的数据，pre表示需要的额外的参数
* 使用
    {{ val | uppercase('pre') }}
* 建议
    简单的操作可以使用过滤器，但是复杂的更建议使用计算属性
    
### *自定义指令 demo12

* 定义指令
    Vue.directive('/* 指令名称 */', function (el, bind) {...});
    el：获取了该指令的dom元素
    bind：使用该指令是的参数
* 获取bind中参数的方法
    打印bind，可以找到bind的相关的内容，
    bind.value获取指令的内容，bind.modifiers获取指令参数
    
### 混合 demo14

* 混合属性的使用
    mixins: [mixin] 使用mixins的来继承其他实例的属性，
    也可以是组件，接受的参数一个数组，可以混合多个
* 注意   
    在使用混合的实例依然可以定义混合对象中已经含有的属性，会重写混合对象的属性
    
## vuex介绍
Vue 的状态管理工具，主要用来实现组件间的通信


## vue-axios介绍  
vue-axios是vue官方推荐的一种http请求工具，作用和ajax类似，只是语法上稍有区别


## vue-router介绍
vue提供的路由工具，主要是vue项目大多有组件组成，使用href的方式跳转并不适合。
vue-router主要有两部分，一是路径，一个是页面渲染的位置，使用vue-router的好处是方便在跳转使进行一些操作


## 扩展的内容（了解）
* nodeJS，npm，Webpack，ES6，elementUI, vue_cli
* Vue Devtools 是vue的调试工具，可以调试生成的vue实例和状态管理工具vuex 

## 项目配置流程
* 进入项目跟目录
* 进入项目目录，安装需要的配置：npm install(有一些依赖需要特殊的环境，比如python等，按需求安装即可)
* 修改项目端口号，修改文件./config/index.js中的28行（port），访问地址：127.0.0.1:9000
* 工程目录创建，不同的文件或功能分配到不同的文件夹下   
|- src/    
|  |- assets/           // 静态文件目录：css、images等   
|  |- components/       // 组件文件目录   
|  |- page/             // 具体业务页面目录   
|  |- router/           // vue-router的路由目录   
|  |- store/            // vuex目录    
|  |- util/             // 工具类目录    
|- main.js              // webpack入口文件    
|- App.vue              // 入口页面    
* 配置路径别名，方便访问，文件./build/webpack.base.conf.js下22行
* 修改编译时的文件名，防止出现各种随机的文件名，文件./bulid/webpack/prod.conf.js
* 配置./config/index.js的第32行的proxyTable，设置跨域访问，这种设置只在开发时好用（[博客:服务端的跨域设置](https://blog.csdn.net/u011517841/article/details/68490586)）
* 使用 npm run build 构建项目 


## 参考文档
* [vue官网](https://cn.vuejs.org/v2/api/)
* [vue-router官网](https://router.vuejs.org/zh/)
* [vuex官网](https://vuex.vuejs.org/zh/)
* [ELEMENT官网](http://element.eleme.io/#/zh-CN/component/installation)

