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