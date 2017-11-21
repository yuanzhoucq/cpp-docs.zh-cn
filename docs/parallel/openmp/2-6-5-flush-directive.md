---
title: "2.6.5 flush 指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1911efe811545c13e62ab9f917ddfc284af35b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="265-flush-directive"></a>2.6.5 flush 指令
**刷新**指令，是否显式或隐式，指定在其实现需要确保团队中的所有线程都具有一个一致的 （在下面指定） 中某些对象视图的"跨线程"序列点内存。 这意味着在完成前面的计算的表达式引用这些对象并随后的计算尚未开始。 例如，编译器必须还原对象的值从寄存器到内存中，并硬件可能需要刷新到内存写入缓冲区并重新加载内存中的对象的值。  
  
 语法**刷新**指令是，如下所示：  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 如果需要同步的对象可以所有指定的变量，则可以在可选中指定这些变量*变量列表*。 如果指针位于*变量列表*、 刷新指针本身、 不是对象指针将指向。  
  
 A**刷新**指令而无需*变量列表*自动存储持续时间与同步除不可访问的对象的所有共享的对象。 (这很可能具有多个开销低于**刷新**与*变量列表*。)A**刷新**指令而无需*变量列表*都隐含具有以下指令：  
  
-   `barrier`  
  
-   在进入和退出**关键**  
  
-   在进入和退出`ordered`  
  
-   在进入和退出**并行**  
  
-   在退出从**为**  
  
-   在退出从**部分**  
  
-   在退出从**单个**  
  
-   在进入和退出**的并行**  
  
-   在进入和退出**并行部分**  
  
 指令不会进行隐式，如果`nowait`子句不存在。 应注意的是，**刷新**指令都不在以下任一项：  
  
-   在进入**为**  
  
-   在进入或退出**master**  
  
-   在进入**部分**  
  
-   在进入**单个**  
  
 访问具有可变限定类型的对象的值的引用的行为方式好像没有**刷新**指令指定该对象在以前的序列点。 修改具有可变限定类型的对象的值的引用的行为方式好像没有**刷新**指令指定该对象在后续的序列点。  
  
 请注意，因为**刷新**指令不具有 C 语言语句作为其语法的一部分，有一些限制它在程序中的放置位置。 请参阅[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式语法。 下面的示例阐释了这些限制。  
  
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
  
 限制到**刷新**指令如下所示：  
  
-   中指定的变量**刷新**指令必须没有引用类型。