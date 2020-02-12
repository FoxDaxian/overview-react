### react


#### 构建相关目录解释

```

react
|
└──scripts
|  |
|  └──rollup
|  |  |  build.js: 
|  |  |  bundles.js: bundleTypes + moduleTypes + 构建入口配置
|  |  |  forks.js: 返回一些依赖，这些依赖是函数，调用的时候根据判断返回不同的结果。
|  |  |  modules.js: 返回四个工具函数
|  |  |  packaging.js: 打包到build中的相关方法
|  |  |  stats.js: 获取文件大小
|  |  |  sync.js: 两个同步方法
|  |  |  utils.js: 暴露工具方法
|  |  |  wrappers.js: 设置通用包裹方法，比如协议、版本号等等
|  |  └──plugins
|  |  |  |  sizes-plugin: 获取gzip压缩后的文件大小
|  |  |  |  use-forks-plugin: 获取forks后的资源？？
|  |  |  |  strip-unused-imports: 获取require中的模块名并返回
|  |    
|  └──shared
|  |    inlinedHostConfigs.js: 由缩写名、入口点、是否开启flow和是否支持服务端 四个字段组成的对象，进而拼接成的数组。

```
> 所有都是亲力亲为嗷。 



render进程简述：

1. 判断节点和callback，并根据结果进行警告
2. 如果是首次绑定的为原生dom，那么创建fiberroot节点
3. 处理callback函数，利用call绑定this，并传入根原生节点
4. 走到下面这个函数
```javascript
unbatchedUpdates(function () {
    updateContainer(children, fiberRoot, parentComponent, callback);
});
```

updateContainer中进行任务调度，包括每个任务的优先级设定，根节点子节点设置，通过链表结构来控制任务队列，流程非常复杂。
未完待续
