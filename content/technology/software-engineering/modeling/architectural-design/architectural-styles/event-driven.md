---
title: '事件驱动风格'
linkTitle: '事件驱动风格'
type: 'docs'
weight: 162322
bookFlatSection: true
bookHidden: false
date: 2023-08-07
isCJKLanguage: true
params:
  author: lyremelody
---

## 1 基本思想
在一个系统中，比如面向对象系统，组件接口提供了访问过程或函数的端口的集合，典型的情况是，组件通过显式地调用这些过程或函数与其他组件交互。然而，另一种可供选择的集成技术非常受关注，它基于隐式调用(implicit invocation)，该技术就是事件驱动的软件架构风格。

**这种风格的基本思想是不直接调用一个过程，而是发布或广播一个或多个事件**。系统中的其他组件通过注册与一个事件关联起来的过程来表示对某一个事件感兴趣。当这个事件发生时，系统本身会调用所有注册了这个事件的过程。这样一个事件的激发会导致其他模块中过程的隐式调用。

**这种风格的主要特点是，事件发布者不知道哪些组件会受到事件的影响**。这样，组件不能对事件的处理顺序或者事件发生后的处理结果做任何假设。正因为这个原因，许多事件驱动系统也包括显式调用(如正常的过程调用)，以此作为组件交互的补充形式。

从架构上来说，事件驱动系统的组件提供了一个过程集合和一组事件。过程可以使用显式的方法进行调用，也可以由组件在系统事件中注册。当触发事件时，会自动引发这些过程的调用。因而在这种架构中，连接件既可以是显式过程调用，也可以是一种绑定事件声明和过程调用的手段。

TODO：补一张事件驱动风格的图

## 2 优点
1. 声明者不需要知道哪些组件会影响事件，组件之间的关联较弱。
2. 提高软件复用能力。只要在系统事件中注册组件的过程，就可以将该组件集成到系统中。
3. 系统便于升级。只要组件名和事件中注册的过程名保持不变，原有组件就可以被新组件替代。

## 3 缺点
1. 组件放弃了对计算的控制权，完全由系统来决定。
   * 当组件触发一个事件时，它不能保证其他组件会对其做出响应。
   * 即使它能够肯定该事件会被其他组件响应，也不知道其他组件是如何对其进行处理的。
2. 存在数据交换问题。
   * 有时数据通过事件传递，但在某些情况下，事件系统必须依赖一个共享缓冲区，以便于数据的交换。
   * 这样，整体的性能和资源的管理可能成为关键性问题。
3. 该风格中正确性验证成为一个问题。
   * 因为发布事件的过程的具体含义与事件激发的上下文有关。
   * 这与传统的过程调用验证不同，当对调用功能行为进行验证时，传统的过程调用只需考虑过程前和过程后的条件。

## 4 应用实例
## 参考资料
1. [《软件架构-理论与实践》](https://book.douban.com/subject/33383454/)
2. [什么是 EDA？，AWS](https://aws.amazon.com/cn/what-is/eda/)