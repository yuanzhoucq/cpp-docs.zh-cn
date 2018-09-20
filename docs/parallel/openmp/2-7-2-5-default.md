---
title: 2.7.2.5 默认 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 047110fe80d15d0ff3d979eeec8abf3e42dc35f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401558"
---
# <a name="2725-default"></a>2.7.2.5 default

**默认**子句，则允许用户以影响变量的数据共享属性。 语法**默认**子句如下所示：

```
default(shared | none)
```

指定**default(shared)** 等效于显式列出中的每个当前可见变量**共享**子句，除非它是**threadprivate**或**缺点**`t`-限定。 在没有显式**默认**子句中，默认行为是相同 if **default(shared)** 指定。

指定**default （none)** 要求至少一个以下必须为每个引用到并行构造的词法范围中的变量，则返回 true:

- 该变量显式列出的一个构造，它包含该引用的数据共享特性子句中。

- 在并行构造声明变量。

- 该变量是**threadprivate**。

- 该变量**const**-限定的类型。

- 变量是循环控制变量的**有关**紧随的循环**为**或**并行的**指令和变量的引用将显示在循环内.

指定一个变量上**firstprivate**， **lastprivate**，或**减少**括住指令子句会导致对该变量的隐式引用封闭上下文。 此类隐式引用也是根据上面列出的要求。

只有一个**默认**上，可以指定子句**并行**指令。

数据共享特性可以通过重写的变量的默认**私有**， **firstprivate**， **lastprivate**，**减少**，并**共享**子句，如下面的示例所示：

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```