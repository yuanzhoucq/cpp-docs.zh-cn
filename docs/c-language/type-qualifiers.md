---
title: 类型限定符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f51dfe3b0b45fb08bc30f9b0d158275112bcf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389980"
---
# <a name="type-qualifiers"></a>类型限定符
类型限定符为标识符提供两个属性之一。 const 类型限定符将对象声明为不可修改。 `volatile` 类型限定符声明一个项，该项的值可由超出该项所在的程序控制范围的某个项（如并发执行的线程）合理更改。  
  
 const 和 `volatile` 这两个类型限定符在声明中只能出现一次。 类型限定符可与任何类型说明符一起出现；但是，它们不能在多项声明中的第一个逗号的后面出现。 例如，以下声明是合法的：  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 以下声明是非法的：  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 仅当访问作为表达式的左值的标识符时，类型限定符才会相关。 有关左值和表达式的信息，请参阅[左值表达式和右值表达式](../c-language/l-value-and-r-value-expressions.md)。  
  
## <a name="syntax"></a>语法  
 *type-qualifier*:  
 constvolatile  
  
 以下是合法的 const 和 `volatile` 声明：  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 如果数组类型的规范包括类型限定符，则将限定元素而不是数组类型。 如果函数类型的规范包括限定符，则行为是不确定的。 `volatile` 和 const 都不会影响值的范围或对象的算术属性。  
  
 此列表描述如何使用 const 和 `volatile`。  
  
-   const 关键字可用于修改任何基本或聚合类型、指向任何类型的对象的指针或 `typedef`。 如果仅使用 const 类型限定符声明项，则项的类型将被当成 const int。可以初始化 const 变量，也可以将该变量置于存储的只读区域中。 const 关键字对于声明指向 const 的指针很有用，因为这需要函数不以任何方式更改指针。  
  
-   编译器假定可通过使用或修改 `volatile` 变量的值未知过程来访问该变量（在程序中的任意未知）。 因此，无论是否在命令行上指定优化，都必须为对 `volatile` 变量的每个分配或引用生成代码，即使它似乎不起作用。  
  
     如果单独使用 `volatile`，则假定 `int`。 `volatile` 类型说明符可用于提供对特定内存位置的可靠访问。 将 `volatile` 用于数据对象，这些对象可通过信号处理程序、并行执行程序或特定硬件（如内存映射的 I/O 控制寄存器）访问或更改。 可以为变量的生存期将变量声明为 `volatile`，也可以将单个引用强制转换为 `volatile`。  
  
-   项可以同时为 const 和 `volatile`，在这种情况下，项无法通过其自己的程序进行合理修改，但可以通过某些异步进程进行修改。  
  
## <a name="see-also"></a>请参阅  
 [声明和类型](../c-language/declarations-and-types.md)