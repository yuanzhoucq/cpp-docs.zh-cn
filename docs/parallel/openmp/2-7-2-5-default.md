---
title: 2.7.2.5 default
ms.date: 11/04/2016
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
ms.openlocfilehash: efb10913b74ebfae37c95d057955c87bdcfca9a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580198"
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