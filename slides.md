---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  供应商服务拆分
drawings:
  persist: false
---

# Supply Server Split

供应商服务拆分

@[zhang13pro](https://github.com/zhang13pro)

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Start <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/zhang13pro" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!-- https://juejin.cn/post/6844903838449664013 -->

---

## 构建工具 🔧

Webpack to Vite

- sass-loader
- css-loader
- ...

<v-click>

```js {monaco}
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: "vue-loader",
      },
      {
        test: /\.(png|jpe?g|gif|svg)(\?.*)?$/,
        loader: "url-loader",
      },
      {
        test: /\.scss$/,
        loaders: ["style", "css", "sass"],
      },
    ],
  },
```

</v-click>

---

Vite ⚡️

- ESModule
- rollup

<v-click>

```js {monaco}
import ...
```

</v-click>

---

## Changes

```bash
下午4:59:53 [vite] warning:
/Users/h/w/supplier-op/src/router/filter.js
1  |  export default function (view) {
2  |      return (resovle) => import(
3  |          `@/views/${view}.vue`
   |          ^
4  |        ).then(resovle)
5  |  }
The above dynamic import cannot be analyzed by vite.
See https://github.com/rollup/plugins/tree/master/packages/dynamic-import-vars#limitations for supported dynamic import formats. If this is intended to be left as-is, you can use the /* @vite-ignore */ comment inside the import() call to suppress this warning.

  Plugin: vite:import-analysis
  File: /Users/h/w/supplier-op/src/router/filter.jsg
下午5:02:39 [vite]
下午5:02:48 [vite] page reload src/plugins/index.js
```

---

## Bug 🐛

Element Table

---

## 升级 Vue3

`Object.defineProperty` to `Proxy`

`Vue` to `createApp`

<v-click>

```js {monaco}
new Vue({
  data: {
    /* options */
  },
})
```

</v-click>

<v-click>

```js {monaco}
createApp(app)
```

</v-click>

<!-- 原型 -->

---

## 规范

[Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "placement"

---

## 生态

<v-click>

Element-plus OR Ant-design-Vue

</v-click>

<v-click>

新的 icons 解决方案

</v-click>

<v-click>

~~新的 CSS 组织方式~~

```html {monaco}
<div w-screen h-screen flex justify-center items-center></div>
<div class="container panel-center item-center"></div>
```

</v-click>

---

Nginx

```bash {monaco}
server {
    listen 80;
    server_name supply.op.baoxiaohe.fun;
    index index.html;
    location / {
        root /home/baoxiaohe/sites/bxh-supplier;
    }

	  location ^~ /api/v2/ {
	      include snippets/proxy.conf;
		    proxy_pass http://bxh-apiv2-dev2/;
	  }

	  location /admin/ {
		    include snippets/proxy.conf;
		    # proxy_pass http://bxh-admin-release/;
		    proxy_pass http://127.0.0.1:7003/;
	  }
    access_log /var/log/nginx/supply.baoxiaohe-access.log;
    error_log /var/log/nginx/supply.baoxiaohe-error.log;
}
```

---

Log

```bash
2022/06/30 14:58:18 [error] 3690692#3690692: *475376 connect() failed (111: Connection refused) while connecting to upstream,
client: 122.233.188.207,
server: supply.baoxiaohe.fun,
request: "GET /admin/captcha_code HTTP/1.1",
upstream: "http://127.0.0.1:7003/captcha_code",
host: "supply.baoxiaohe.fun",
referrer: "http://supply.baoxiaohe.fun/"
```
