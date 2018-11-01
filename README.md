
# (vue.js)nuxt.js:IP端口/局域网配置
 
 @[TOC](目录)
### 一、Nuxt安装与运行
作为一个使用Nuxt开发的新手，在配置局域网访问之前，先回顾一下Nuxt的快速安装。根据在【[Nuxt官网](https://zh.nuxtjs.org/guide/installation)】的安装说明，在安装的过程中会有一些配置，可以根据个人需要进行处理。另外说明，如果电脑还没有安装npx的，自行去安装。我的安装和配置见下图：
![图一](https://img-blog.csdnimg.cn/20181101113709783.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
见到下图的内容，就说明项目安装成功：
![图二](https://img-blog.csdnimg.cn/20181101113803311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
这时候就可以直接根据框内的说明启动项目了：
![图三](https://img-blog.csdnimg.cn/20181101115200737.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
在浏览器上输入本地访问地址：
![图四](https://img-blog.csdnimg.cn/2018110111535374.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

从以上整个流程来看没有一点问题，对不对，说明我们新建的【demo1】项目样板成功了。但是，这时候我想通过ip地址访问页面，就会出现如下页面：
![图五](https://img-blog.csdnimg.cn/2018110112003989.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

无法访问此网站！！！懵逼了，怎么办怎么办怎么办～

这时候当然是要做ip地址的配置了，在此之前，说明一下，我要用【[WebStorm](https://www.jetbrains.com/webstorm/)】开发项目了～开发项目了～开发项目了～
重要的事情说三遍。

### 二、IP端口冲突问题
使用【WebStorm】打开项目后，直接打开项目运行：
![图六](https://img-blog.csdnimg.cn/20181101143322373.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
又来了一个问题 ？？？这又是什么情况，刚才在终端上运行都没有错，对不对？
经过分析，是端口被占用了，那还是ip地址的问题（因为我在用WebStorm打开本demo前，还打开了其他demo，真是尴尬）。这时候越来越说明配置ip地址的迫切性和必要性了，以后要是开启多个项目开发时会搞死自己啊。那我们就开启配置IP地址之路吧。

### 三、端口/局域网配置

作为Nuxt的菜鸟，怎么处理这问题？caca，还是看得官方文档，无限浏览博客借鉴别人的经验啊。经过千辛万苦，不懈努力，终是苦尽甘来，让我找到了两个方法用来配置IP端口/局域网访问的方法。

#### 1、在[package.json]文件中配置
**1、查看package.json已有配置**
在【package.json】文件中增加一些配置，在增加配置之前，先看一下新建项目在给文件中一些已有的配置：
```js
{
  "name": "demo1",
  "version": "1.0.0",
  "description": "My awe-inspiring Nuxt.js project",
  "author": "rattanchen",
  "private": true,
  "scripts": {
    "dev": "nuxt",
    "build": "nuxt build",
    "start": "nuxt start",
    "generate": "nuxt generate"
  },
  "dependencies": {
    "cross-env": "^5.2.0",
    "nuxt": "^2.0.0",
    "@nuxtjs/axios": "^5.0.0"
  },
  "devDependencies": {
    "nodemon": "^1.11.0"
  }
}

```
**2、增加配置**
我们只要在这个项目中添加如下配置,端口可以自己改：

```js
  "config": {
    "nuxt": {
      "host": "0.0.0.0",
      "port": "8011"
    }
  },
```
配置好之后的文件见下图：
![图七](https://img-blog.csdnimg.cn/2018110113183020.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

**3、启动示例**
然后直接运行项目就可以了，见下图：
![图八](https://img-blog.csdnimg.cn/20181101131918140.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

访问ip地址见下图：

![图九](https://img-blog.csdnimg.cn/20181101131955835.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

再写一个测试示例：
```vue
<template>
  <div>
    <h1 class="center">
      Hello Nuxt !
    </h1>
  </div>
</template>

<script>
  export default {
    name: "test"
  }
</script>

<style scoped>
  h1.center{
    margin-top: 50%;
    text-align: center;
  }

</style>

```

访问结果：

![图十](https://img-blog.csdnimg.cn/20181101132409235.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)


#### 2、在[servrt.index]文件中配置
**1、增加文件并配置**
在项目的根目录下创建【server】文件夹，并在改文件夹中创建【index.js】文件：
![图十一](https://img-blog.csdnimg.cn/20181101132744312.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

然后在【index.js】复制一下代码：

```js

const express = require('express')
const consola = require('consola')
const { Nuxt, Builder } = require('nuxt')
const app = express()
const host = process.env.HOST || '0.0.0.0'
// 端口号（这里换个端口号测试）
const port = process.env.PORT || 33333

app.set('port', port)

// Import and Set Nuxt.js options
let config = require('../nuxt.config.js')
config.dev = !(process.env.NODE_ENV === 'production')

async function start() {
  // Init Nuxt.js
  const nuxt = new Nuxt(config)

  // Build only in dev mode
  if (config.dev) {
    const builder = new Builder(nuxt)
    await builder.build()
  }

  // Give nuxt middleware to express
  app.use(nuxt.render)

  // Listen the server
  app.listen(port, host)
  consola.ready({
    message: `Server listening on http://${host}:${port}`,
    badge: true
  })
}
start()

```
**2、修改package.json文件配置**
在【package.json】文件中,将【scripts.dev】的值改成：
```json
cross-env NODE_ENV=development nodemon server/index.js --watch server
```

运行后见下图：
![图十二](https://img-blog.csdnimg.cn/20181101133831767.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

### 四、下载安装Demo

#### 1、下载地址
在这里，我上传了一个demo，欢迎点击下载
a、[Gitee下载](https://gitee.com/chenzm_186/domain_name_visit)
b、[GitHub下载](https://github.com/chzm/domain_name_visit)
c、[CSDN资源下载](https://download.csdn.net/my)
#### 2、npm安装
在demo下载之后，用WebStorm工具打开，这时候右下角会有如下提示：
![图十三](https://img-blog.csdnimg.cn/20181101153742357.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
意思是让我们在终端里执行【npm install】，或者直接点击该蓝色位置会自动安装。这是因为，我在上传demo的时候，【node_modules】目录下的文件加起来有一百多兆，太大了，为避免上传下载的麻烦，所以先把他删了：
![图十四](https://img-blog.csdnimg.cn/20181101154344476.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

待终端出现下图，说明npm安装成功：
![图十五](https://img-blog.csdnimg.cn/20181101154603217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)

#### 3、运行[WebStorm]的配置
安装成功之后，即可直接运行demo，作为一个新手，这里在啰嗦一下，运行项目的配置顺序：
![图十六](https://img-blog.csdnimg.cn/20181101155816361.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)


![图十八](https://img-blog.csdnimg.cn/2018110115583376.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)


![图十九](https://img-blog.csdnimg.cn/20181101155847874.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)
运行成功：
![图二十](https://img-blog.csdnimg.cn/20181101161031745.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODYzMzY1OQ==,size_16,color_FFFFFF,t_70)


### 五、补充
另外，我还发现有人使用其他的方式解决了这个问题，但是我试过了不行，可以了解一下：
1、[VUE 如何配置localhost和IP 都可以访问](https://segmentfault.com/q/1010000014797068)
2、[使用vue-cli的webpack-simple模板，如何配置webpack-dev-server可以局域网访问？](https://segmentfault.com/q/1010000008336132/a-1020000008342121)
如果有解决的读者，可以留言分享一下哈～


**解决了问题，是不是很开心很激动？！如果有用的话，～～欢迎点赞～～**

---

**参考链接：**

1、[Nuxt官网](https://zh.nuxtjs.org/guide/installation)
2、[(vue.js)nuxtjs不能通过域名或其他ip访问，是什么原因？](http://www.codes51.com/itwd/4380433.html)
3、[解决vue-cli构建本地项目，无法通过本机ip访问的问题](https://blog.csdn.net/example440982/article/details/81005258)


