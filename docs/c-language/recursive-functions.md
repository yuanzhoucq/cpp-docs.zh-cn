---
title: "递归函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fcbe38eb67a31f6bb62750b44df57aa9d64b9272
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recursive-functions"></a>递归函数
C 程序中的任何函数都可以以递归方式调用；也就是说，函数可以调用自己。 递归调用的数量受堆栈的大小的限制。 有关设置堆栈大小的链接器选项的信息，请参阅 [/STACK（堆栈分配）](../build/reference/stack-stack-allocations.md)(/STACK) 链接器选项。 每次调用函数时，都会为参数以及 auto 和 register 变量分配新存储，以便不会覆盖它们在前面未完成的调用中的值。 只有从中创建参数的函数的实例才能直接访问该参数。 前面的参数对函数的后续实例不可直接访问。  
  
 请注意，使用 static 存储声明的变量在每次递归调用时不需要新存储。 它们的存储在程序的生存期内存在。 每次引用此类变量时都将访问相同的存储区域。  
  
## <a name="example"></a>示例  
 本示例演示了递归调用：  
  
```  
int factorial( int num );      /* Function prototype */  
  
int main()  
{  
    int result, number;  
    .  
    .  
    .  
    result = factorial( number );  
}  
  
int factorial( int num )      /* Function definition */  
{  
    .  
    .  
    .  
    if ( ( num > 0 ) || ( num <= 10 ) )  
        return( num * factorial( num - 1 ) );  
}  
  
```  
  
## <a name="see-also"></a>请参阅  
 [函数调用](../c-language/function-calls.md)