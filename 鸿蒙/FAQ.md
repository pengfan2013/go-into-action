## 架构

1. 模块化有哪些实体结构, 各层怎么组合的?
- app app.json5描述
- module 拆分这个层级作用是什么? module.json5描述
- Ability 
  - 分为UIAbility 绑定了窗口实例
  - ExtensionAblity 拆分这个层级作用是什么?
- Component
  - 被Entry装饰的组件 绑定了页面实例
  - 自定义组件
  - 官方组件

2. 业务基本粒度是什么? Component么? 基本粒度内包含哪些实体结构?
  - UI 布局和样式怎么表达
  - 事件模型
  - 状态管理
  - 生命周期
  - 渲染UI

3. 组件状态管理采用的什么? 数据流怎么设计? 双向绑定怎么解决?
  - 组件状态
  - 状态父子组件共享
  - 状态跨组件共享

4. 应用状态管理采用的什么? 数据持久化? 如何从数据库到Ability再到Component?
  - 页面间的状态管理为什么在这里处理
  - 什么状态需要持久化存储
  - 页面级别的UI状态存储是LocalStorage, 那么什么状态需要用LocalStorage来处理什么状态需要用组件跨层级传递来处理?
  - 应用级别的UI状态存储是APPStorage

5. ArkTS看起来缺乏更细一层级的封装状态和方法的粒度实体, 缺少Service这样的依赖注入组织业务逻辑的结构, 或者说缺少Hook API这种形式. 
  - 业务逻辑组件(无实际UI build)
  - 是否可以手动实现自定义的@Service装饰器, 用来装饰空Class, 用来组织业务逻辑?

6. 目前看起来工具层级提供了单向绑定和双向绑定组织状态, 整体上应该如何限制状态的混乱?
  - 整体上单向数据流
  - state + update state method 向下单向数据流
  - 无UI的业务组件, 就可以以Provide/Consume的形式来组织业务逻辑. 所以如何构建无UI组件? 有什么限制

7. 自定义组件模版渲染更细粒度辅助, 类似与vue slot或者JSX props render对应的概念是 @BuilderParam @Builder, 对应如何使用?

8. ArkTS事件模型是如何设计的?

9. 模块功能分层架构


## UI描述

1. transition实现

2. 如何实现类似插槽的功能?
 - @Builder和@BuilderParam 类型配对设置一个build函数位置. 多个就用多组@BuilderParam
 - 有且仅有一组@BuilderParam时, 可以用<尾随闭包初始化组件>, 即组件后紧跟大括号, 作为生成.

 - 构建函数的封装直接用@Builder
 - 状态封装用的Class, viewmodel
 - 状态State+构建函数@Builder封装 -> 组件Component
 - 构建函数@Builder+成员函数封装 -> 