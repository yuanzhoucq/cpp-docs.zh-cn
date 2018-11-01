---
title: 2.7.2.6 reduction
ms.date: 11/04/2016
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
ms.openlocfilehash: 54b326feb4e4ccf1f1da5c8152ffc8d1e4bd13b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456012"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

此子句中出现的标量变量上执行减少*变量列表*，使用运算符*op*。 语法`reduction`子句如下所示：

> 减少 (*op*:*变量列表*)

减少通常指定为具有以下形式之一的语句：

> *x* = *x* *op* *expr*
> *x* *binop* =*expr*
> *x* = *expr* *op* *x* （除外表示减法） *x*++
> ++*x*
> *x*--
> --*x*

其中：

*x*<br/>
一个指定在缩减变量`list`。

*variable-list*<br/>
以逗号分隔的标量降低变量列表。

*expr*<br/>
具有未引用的标量类型的表达式*x*。

*操作*<br/>
不是重载的运算符，但其中一个 +， &#42;、-， &amp;，^， &#124;， &amp; &amp;，或&#124; &#124;。

*binop*<br/>
不是重载的运算符，但其中一个 +， &#42;、-， &amp;，^，或&#124;。

以下是一种`reduction`子句：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

该示例中所示，操作员可能被隐藏在函数调用。 用户应小心运算符中指定`reduction`子句与相匹配的缩减运算。

尽管的右操作数&#124;&#124;运算符在此示例中没有任何副作用，它们允许使用，但应谨慎使用。 在此上下文中，确保不能在循环的顺序执行过程中发生的副作用可能会并行执行期间发生。 由于执行迭代的顺序是不确定，可能出现这种差异。

运算符用来确定编译器用于减少任何私有变量的初始值和来确定终止运算符。 显式指定运算符允许减少语句要构造的词法范围之外。 任意数量的`reduction`子句可指定指令，但变量可能会出现在最多一个`reduction`该指令的子句。

在每个变量的私有副本*变量列表*创建，另一个用于每个线程，如同`private`已使用子句。 根据运算符初始化的私有副本 （请参阅下表）。

为其区域末尾`reduction`指定子句，原始对象更新以反映组合其原始值与使用指定的运算符的私有副本的最终值的结果。 减少运算符可以 （除外减）、 所有结合使用，编译器可以自由地重新关联的最终值的计算。 （减法减少的部分结果添加引号以形成的最终值。

第一个线程到达包含子句和减少计算完成前保持时，原始对象的值将成为不确定。  通常情况下，计算会构造; 结束时完成但是，如果`reduction`向其构造上使用子句`nowait`是还应用，原始对象的值保持不确定执行屏障同步以确保所有线程都完成才`reduction`子句。

下表列出了有效的运算符和其规范初始化值。 实际初始化值将为使用 reduction 变量的数据类型一致。

|运算符|初始化|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

对限制`reduction`子句如下所示：

- 中的变量的类型`reduction`子句必须是有效的 reduction 运算符，不同之处在于永远不会允许使用指针类型和引用类型。

- 中指定的变量`reduction`子句不能**const**-限定。

- 专用并行区域内或在中都出现的变量`reduction`子句**并行**指令不能指定`reduction`绑定到并行构造的工作共享指令上的子句。

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```
