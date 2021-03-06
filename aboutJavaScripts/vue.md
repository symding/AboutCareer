#### install
```
cnpm install -g @vue/cli
```

#### `vue create`
```bash
# 项目名称不能使用大写字母
vue create project-name
```

#### `vue-router`
> [vue-rouyer](https://router.vuejs.org/zh/installation.html)

##### 基本使用
```html
<script src="https://unpkg.com/vue@3"></script>
<script src="https://unpkg.com/vue-router@4"></script>

<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!--使用 router-link 组件进行导航 -->
    <!--通过传递 `to` 来指定链接 -->
    <!--`<router-link>` 将呈现一个带有正确 `href` 属性的 `<a>` 标签-->
    <router-link to="/">Go to Home</router-link>
    <router-link to="/about">Go to About</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
</div>
<script>
    // 1. 定义路由组件.
    // 也可以从其他文件导入
    const Home = { template: '<div>Home</div>' }
    const About = { template: '<div>About</div>' }

    // 2. 定义一些路由
    // 每个路由都需要映射到一个组件。
    // 我们后面再讨论嵌套路由。
    const routes = [
    { path: '/', component: Home },
    { path: '/about', component: About },
    ]

    // 3. 创建路由实例并传递 `routes` 配置
    // 你可以在这里输入更多的配置，但我们在这里
    // 暂时保持简单
    const router = VueRouter.createRouter({
    // 4. 内部提供了 history 模式的实现。为了简单起见，我们在这里使用 hash 模式。
    history: VueRouter.createWebHashHistory(),
    routes, // `routes: routes` 的缩写
    })

    // 5. 创建并挂载根实例
    const app = Vue.createApp({})
    //确保 _use_ 路由实例使
    //整个应用支持路由。
    app.use(router)
    app.mount('#app')   
</script>
```

#### 组件传值
* 引用组件
```vue
<hello-world :testname="testvalue"></hello-world>
```
* 被引用组件
```js
<template><p> {{testname }}</p></template>
<scripts>
  export default {
    name: 'App',
    props: {
      testname: String
    },
</scripts>
```