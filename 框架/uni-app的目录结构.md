#### uni-app的目录结构

┌─components            uni-app组件目录

 │  └─comp-a.vue         可复用的a组件

 ├─hybrid                存放本地网页的目录，[详见](https://uniapp.dcloud.io/component/web-view) 

├─platforms             存放各平台专用页面的目录，[详见](https://uniapp.dcloud.io/platform?id=整体目录条件编译) 

├─pages                 业务页面文件存放的目录 

│  ├─index 

│  │  └─index.vue       index页面 

│  └─list 

│     └─list.vue        list页面 

├─static                存放应用引用静态资源（如图片、视频等）的目录，**注意：**静态资源只能存放于此 ├─wxcomponents          存放小程序组件的目录，[详见](https://uniapp.dcloud.io/frame?id=小程序组件支持) 

├─main.js               Vue初始化入口文件 

├─App.vue               应用配置，用来配置App全局样式以及监听 [应用生命周期](https://uniapp.dcloud.io/frame?id=应用生命周期) 

├─manifest.json         配置应用名称、appid、logo、版本等打包信息，[详见](https://uniapp.dcloud.io/collocation/manifest) 

└─pages.json            配置页面路由、导航条、选项卡等页面类信息，[详见](https://uniapp.dcloud.io/collocation/pages)



##### Tips

+ static目录下的js文件不会被编译，如果有es6的代码，不经过转换直接运行，在手机设备上会报错
+ css、less/scss等资源同样不要放在static目录下。建议使用公用的资源放在common目录下
+ HbuilderX 1.90+支持在根目录创建ext.json、sitemap.json文件





#### 资源路径说明

##### 模板内引入静态资源

template内引入静态资源，如image、video等标签的src属性时，可以使用相对路径或者绝对路径

<!-- 绝对路径，/static指根目录下的static目录，在cli项目中/static指src目录下的static目录 --> <image class="logo" src="/static/logo.png"></image> 

<image class="logo" src="@/static/logo.png"></image> 

<!-- 相对路径 --> 

<image class="logo" src="../../static/logo.png"></image>

##### 注意

+ @开头的绝对路径以及相对路径会经过base64转换校检规则
+ 引入的静态资源在非h5平台，均不会转换成base64
+ H5平台，小于4kb的资源会被转换成base64，其余不转



#### js文件引入

js文件或者script标签内，包括render.js引入js文件时，可以使用相对路径或者绝对路径，形式如下：

// 绝对路径，@指向项目根目录，在cli项目中@指向src目录

```javascript
import add from '@/common/add.js'
```

// 相对路径

```javascript
 import add from '../../common/add.js'
```

**js文件不支持使用/开头的方式引入**