## 描述

1. 描述一些需求（子类型多态）
2. 描述要求存在（有限多态）
3. 描述特定情况（特设多态）
4. 显示要求标注实现
  4.a. 可批量标注（大多依赖泛型）
5. 不要求标注实现（鸭子类型）（结构类型）（行多态）
6. 提供默认实现


php 的 trait，
oc 的 interface 属于 6
oc 的 protocol 属于 1, 4
go，typescript 的 interface 属于 1, 5
java c# 等的 interface 属于 1, 4, 6
js 的 protocol 提案 属于 1, 2, 4
c艹 的 concept 属于 2, 3, 5
Haskell 的 typeclass，c# 的 concept 提案 属于 2, 3, 4, 4.a
swift 的 protocol, rust 的 trait，scala 的 trait 属于 1, 2, 3, 4, 4.a, 6

## TS中的概念

protocol + interface 加起来实现了1, 2, 4, 5, 6的特性.
protocol 用于描述需求，interface 用于描述实现.

例如 iteration protocol, 用于描述一个对象是否可以被迭代，但是不要求实现，只要求描述.

Array.from, Map和Set构造函数, 结构语法[...], for of语法, 都是围绕这个protocol的.

String, Array, Map, Set, TypedArray, 这些就是上一个描述中的6, 提供了默认实现.