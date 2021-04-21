可供参考

https://blog.csdn.net/shentibeitaokong/article/details/83039021

https://juejin.cn/post/6844903517564436493

https://www.jianshu.com/p/550ab0dafd91

1. 添加依赖 svg-sprite-loader  svgo

2. 在src目录下新建icons目录，icons——>svg（存放svg图）   icons——>index.js    icons——>svgo.yml

3. index.js文件

```js
import Vue from 'vue'
import SvgIcon from '@/components/SvgIcon'// svg component

// register globally(注册全局组件)
Vue.component('svg-icon', SvgIcon)

const req = require.context('./svg', false, /\.svg$/)
const requireAll = requireContext => requireContext.keys().map(requireContext)
requireAll(req)
```

​    svgo.yml

```yaml
# replace default config

# multipass: true
# full: true

plugins:

  # - name
  #
  # or:
  # - name: false
  # - name: true
  #
  # or:
  # - name:
  #     param1: 1
  #     param2: 2

- removeAttrs:
    attrs:
      - 'fill'
      - 'fill-rule'

```

4. 封装icon，在components下新建SvgIcon文件

index.vue文件内容

```vue
<template>
  <div v-if="isExternal" :style="styleExternalIcon" class="svg-external-icon svg-icon" v-on="$listeners" />
  <svg v-else :class="svgClass" aria-hidden="true" v-on="$listeners">
    <use :href="iconName" />
  </svg>
</template>

<script>
// doc: https://panjiachen.github.io/vue-element-admin-site/feature/component/svg-icon.html#usage
import { isExternal } from '@/utils/validate'

export default {
  name: 'SvgIcon',
  props: {
    iconClass: {
      type: String,
      required: true
    },
    className: {
      type: String,
      default: ''
    }
  },
  computed: {
    //判断是否为外部引入的
    isExternal() {
      return isExternal(this.iconClass)
    },
    iconName() {
      return `#icon-${this.iconClass}`
    },
    svgClass() {
      if (this.className) {
        return 'svg-icon ' + this.className
      } else {
        return 'svg-icon'
      }
    },
    styleExternalIcon() {
      return {
        mask: `url(${this.iconClass}) no-repeat 50% 50%`,
        '-webkit-mask': `url(${this.iconClass}) no-repeat 50% 50%`
      }
    }
  }
}
</script>

<style scoped>
.svg-icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

.svg-external-icon {
  background-color: currentColor;
  mask-size: cover!important;
  display: inline-block;
}
</style>

```

5. 在vue.vonfig.js（vuecli4）中/webpack.base.conf.js（vuecli2）中

   ```js
   const path = require('path'); //引入path模块
   function resolve(dir) {
       return path.join(__dirname, dir) //path.join(__dirname)设置绝对路径
   }
   module.exports = {
       configureWebpack: {
           resolve: {
               alias: {
                   '@': resolve('src'),
                   'assets': resolve('src/components/assets'),
                   'components': resolve('src/components'),
                   'views': resolve('src/views'),
                   'network': resolve('src/network'),
                   'common': resolve('src/common'),
                   'layout': resolve('src/layout'),
               }
           }
       },
       chainWebpack: (config) => {
           // set svg-sprite-loader
           config.module
               .rule('svg')
               .exclude.add(resolve('src/assets/icons'))
               .end()
           config.module
               .rule('icons')
               .test(/\.svg$/)
               .include.add(resolve('src/assets/icons'))
               .end()
               .use('svg-sprite-loader')
               .loader('svg-sprite-loader')
               .options({
                   symbolId: 'icon-[name]'
               })
               .end()
       }
   }
   ```

   

6. 使用

   icon-class为svg的名字

   ```vue
   <svg-icon :icon-class="iexit-fullscreen" @click="click" />
   ```

   