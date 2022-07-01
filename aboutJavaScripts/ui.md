#### `element-UI`
```
cnpm i element-ui -S
```

##### 编程式导航
 通过 访问Vue路由链接并渲染至 `<route-view>`
```html
<script>
    export default {
    name: 'App',
    methods:{
        toTest:function(){
        this.$router.push({path:"/test"})  // 就是这一句，注意是router，不是route
        }
    }
    }
</script>
```
