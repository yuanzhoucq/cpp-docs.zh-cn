---
title: 2.6.5 flush 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d67453b636d50fcb78092318ebb76f5192817548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442729"
---
# <a name="265-flush-directive"></a>2.6.5 flush 指令

**刷新**指令，无论是显式还是暗示的保证，指定"跨线程"序列点的实现需要确保团队中的所有线程都都一致 （在下面指定） 中某些对象视图内存。 这意味着，以前计算的表达式引用这些对象的已完成，随后的计算尚未开始。 例如，编译器必须还原对象的值从注册到内存，而硬件可能需要刷新写入缓冲区内存并重新加载内存中的对象的值。

语法**刷新**指令是按如下所示：

```
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步的对象可以所有指定的变量，则这些变量可以指定可选*变量列表*。 如果指针是否位于*变量列表*，指针本身会刷新，不是对象指针将指向。

一个**刷新**指令而无需*变量列表*将包括无法访问对象的所有共享的对象同步与自动存储持续时间。 (这是可能需要考虑更多的开销比**刷新**与*变量列表*。)一个**刷新**指令而无需*变量列表*默示针对以下指令：

- `barrier`

- 在进入和退出**关键**

- 在进入和退出 `ordered`

- 在进入和退出**并行**

- 在退出**为**

- 在退出**部分**

- 在退出**单一**

- 在进入和退出**并行的**

- 在进入和退出**并行部分**

指令不隐式，如果`nowait`子句。 应注意的是，**刷新**指令不隐式表示以下任一项：

- 在进入**为**

- 在进入或退出**master**

- 在进入**部分**

- 在进入**单一**

访问具有可变限定类型的对象的值的引用的行为就好像**刷新**指令指定在上一个序列点的对象。 修改具有可变限定类型的对象的值的引用的行为就好像**刷新**指令指定该对象在后续序列点。

请注意，由于**刷新**指令不具有 C 语言语句作为其语法的一部分，有一些限制其放置在程序中。 请参阅[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式语法。 下面的示例说明了这些限制。

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

限制**刷新**指令如下所示：

- 中指定的变量**刷新**指令不能是引用类型。