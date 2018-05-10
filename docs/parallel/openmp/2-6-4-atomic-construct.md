---
title: 2.6.4 atomic 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66f0dc8469d1d70b2697df1fe120f10142d90dbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="264-atomic-construct"></a>2.6.4 atomic 构造
`atomic`指令可确保特定内存位置而不是将其公开到的多个可能性的更新是以原子方式，同时编写线程。 语法`atomic`指令是，如下所示：  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 表达式语句必须具有以下形式之一：  
  
 *x binop*= *expr*  
  
 x + +  
  
 + + x  
  
 x-  
  
 --x  
  
 在前面的表达式：  
  
-   *x*是具有标量类型的左值表达式。  
  
-   *expr*是标量类型的表达式，它不引用指定的对象*x*。  
  
-   `binop` 而不是重载的运算符之一的 +、 *、-、 /、 &、 ^， &#124;，<\<，或 >>。  
  
 尽管它是实现定义是否实现替换所有`atomic`指令与**关键**指令具有相同的唯一*名称*、`atomic`指令允许更好的优化。 提供了通常硬件说明可以执行开销最少的原子更新。  
  
 负载和指定的对象的存储区*x*是原子; 的评估*expr*不是原子的。 若要避免争用条件，应该用进行保护的并行中的位置的所有更新`atomic`指令，除了那些认为是免费的争用条件。  
  
 限制到`atomic`指令如下所示：  
  
-   在整个程序的存储位置 x 的所有原子引用都需要有兼容的类型。  
  
## <a name="examples"></a>示例：  
  
```  
extern float a[], *p = a, b;  
/* Protect against races among multiple updates. */  
#pragma omp atomic  
a[index[i]] += b;  
/* Protect against races with updates through a. */  
#pragma omp atomic  
p[i] -= 1.0f;  
  
extern union {int n; float x;} u;  
/* ERROR - References through incompatible types. */  
#pragma omp atomic  
u.n++;  
#pragma omp atomic  
u.x -= 1.0f;  
```