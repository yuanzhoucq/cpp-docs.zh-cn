---
title: "2.6.4 atomic 构造 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.4 atomic 构造
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

 `atomic` 指令可确保特定的内存位置，而不是将其公开到多个可能性以原子方式更新同时编写线程。 语法 `atomic` 指令是，如下所示︰  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 表达式语句必须具有以下形式之一︰  
  
 *x binop*= *expr*  
  
 x + +  
  
 + + x  
  
 x-  
  
 --x  
  
 在前面的表达式︰  
  
-   *x* 是具有标量类型的左值表达式。  
  
-   *expr* 是具有标量类型的表达式，也不引用指定的对象 *x*。  
  
-   `binop` 重载的运算符并不是 +、 *、-、 /、 &、 ^，（& a) #124;，<\<，或 >>。  
  
 尽管它是由实现定义是否实现将替换所有 `atomic` 指令与 **关键** 指令具有相同的唯一 *名称*, 、 `atomic` 指令允许更好地优化。 提供了通常硬件说明，可以执行系统开销最少的原子更新。  
  
 只有负载和指定的对象的存储区 *x* 是原子; 计算 *expr* 不是原子的。 若要避免出现争用情况，应使用进行保护并行中的位置的所有更新 `atomic` 指令时，除了那些已知都是免费的争用条件。  
  
 限制 `atomic` 指令如下所示︰  
  
-   对在整个程序的存储位置 x 的所有原子引用需要具有兼容的类型。  
  
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