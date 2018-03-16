---
title: "2.7.2.6 缩减 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 684067eae668398e71ca4ace0cc136e3210e0dbf
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

此子句对出现在标量变量执行减少*变量列表*，与运算符*操作*。 语法`reduction`子句是，如下所示：

> 减少 (*操作*:*变量列表*)

减少通常指定为具有以下形式之一的语句：

> *x* = *x* *op* *expr*  
> *x* *binop* = *expr*  
> *x* = *expr* *操作* *x* （除外减法）  
> *x*++  
> ++*x*  
> *x*--  
> --*x*  

其中：

*x*  
指定在缩减变量之一`list`。

*variable-list*  
以逗号分隔的标量降低变量列表。

*expr*  
具有未引用的标量类型的表达式*x*。

*op*  
不是重载的运算符但其中一个 +、 &#42;、-， &amp;，^， &#124;， &amp; &amp;，或&#124; &#124;。

*binop*  
不是重载的运算符但其中一个 +、 &#42;、-， &amp;，^，或&#124;。

以下是一种`reduction`子句：  
  
```cpp  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
该示例中所示，操作员可能被隐藏函数调用中。 用户应小心运算符中指定`reduction`子句与相匹配的缩减运算。

尽管的右操作数&#124;&#124;运算符在此示例中没有任何副作用，它们允许使用，但应谨慎使用。 在此上下文中，在并行执行可能会不保证在循环的顺序执行过程中发生的副作用。 由于执行的迭代的顺序是不确定，可能出现这种差异。

运算符用来确定编译器用于减少任何私有变量的初始值，和来确定终止运算符。 显式指定运算符允许减少语句之外的构造的词法范围。 任意数量的`reduction`子句可指定在指令，但变量可能会出现在最多一个`reduction`该指令的子句。

在每个变量的私有副本*变量列表*创建后，一个用于每个线程，就像`private`已使用子句。 私有副本初始化根据运算符 （请参阅下表）。

在为其区域末尾`reduction`指定了子句，原始对象更新以反映组合使用指定的运算符的私有副本的最终值使用其原始值的结果。 缩减运算符是 （除外减法），所有关联，编译器可能自由地重新关联的最终值的计算。 （减法缩减的部分结果被添加到窗体的最终值。）

当第一个线程达到包含子句并保持缩减计算完成之前，原始对象的值将成为不确定。  通常情况下，计算将完成构造; 末尾但是，如果`reduction`向其构造上使用子句`nowait`是另外应用原始对象的值将一直不确定执行屏障同步以确保所有线程均已都完成`reduction`子句。

下表列出了有效的运算符和其规范的初始化值。 实际初始化值将与 reduction 变量的数据类型一致。

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

- 中的变量的类型`reduction`子句必须是有效的 reduction 运算符，只不过永远不会允许使用指针类型和引用类型。

- 中指定的变量`reduction`子句不能**const**-限定。

- 变量的是专用的并行区域内或出现在`reduction`子句**并行**指令不能指定`reduction`将绑定到并行构造工作共享指令上的子句。

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
