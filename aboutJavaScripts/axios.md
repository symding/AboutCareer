> [axios](http://www.axios-js.com/)

##### install
```bash
npm install axios
```

#### &vue
```javascript
import Vue from 'vue'
import http from 'axios'
Vue.prototype.$http = http
new Vue({
  router,
  render: h => h(App),
}).$mount('#app')
```

#### post && get
**post** 使用 `data` 参数，**get** 使用 `params` 参数
```javascript
axios.request({
        url: 'URL',
        method: 'get',
        params: param
    }
axios.request({
        url: 'URL',
        method: 'post',
        data: param,
```