### [fiber](https://github.com/acdlite/react-fiber-architecture)

#### 对于fiber来说我们有几个目标 


1. 随时暂停任务，并可以稍后继续执行
1. 对不同类型的任务进行权重的赋予
1. 复用之前已完成的任务(结果)
1. 如果一个任务不再需要了，我们可以随时终止它

也就是说，我们需要实现一个自己的函数调用堆栈



### 打包构建

- 使用workspace，可以直接加载所有本地包，比如使用require。

#### 流程概述
1. 统一处理Bundles导出的各个版本、平台的react
2. for ... of 循环Bundles
  ```javascript
     {
       bundleTypes: [
         UMD_DEV,
         UMD_PROD,
         UMD_PROFILING,
         NODE_DEV,
         NODE_PROD,
         FB_WWW_DEV,
         FB_WWW_PROD,
         FB_WWW_PROFILING,
       ],
       moduleType: ISOMORPHIC,
       entry: 'react',
       global: 'React',
       externals: [],
     },
  ```
3. 根据Bundles的信息生成rollup配置
4. 判断是否为watch模式
5. 同步资源，比如吧packages中react包中的package.json、LICENSE、readme等复制到各react的rollup产出对应包中
6. npm pack


### react常用包都是用来做什么的

- react：
  react包仅仅包含定义react组件所必要的方法，通常会和react渲染器一起使用，比如 web端的react-dom 和 na端的react-native
  换句话说，react暴露出很多基础核心方法
- react-dom：
  react-dom作为浏览器或者服务端的入口点，一般与react配合使用
  换句话说，react-dom用来将react创建的元素，比如react-element挂载到页面中或者产出dom字符串供服务端使用




### 查漏补缺

#### 常见进制数的表示
- 十进制： 无前缀
- 八进制：前缀0o | 0O
- 十六进制：前缀0x | 0X
- 二进制：0b、0B
