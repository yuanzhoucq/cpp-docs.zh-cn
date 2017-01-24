---
title: "递归函数 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "函数调用, 递归的"
  - "函数 [C], 递归调用"
  - "函数 [C], 递归的"
  - "递归函数调用"
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 递归函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 程序中的任何函数都可以以递归方式调用；也就是说，函数可以调用自己。  递归调用的数量受堆栈的大小的限制。  有关设置堆栈大小的链接器选项的信息，请参阅 [\/STACK（堆栈分配）](../build/reference/stack-stack-allocations.md) \(\/STACK\) 链接器选项。  每次调用函数时，都会为参数以及 **auto** 和 **register** 变量分配新存储，以便不会覆盖它们在前面未完成的调用中的值。  只有从中创建参数的函数的实例才能直接访问该参数。  前面的参数对函数的后续实例不可直接访问。  
  
 请注意，使用 **static** 存储声明的变量在每次递归调用时不需要新存储。  它们的存储在程序的生存期内存在。  每次引用此类变量时都将访问相同的存储区域。  
  
## 示例  
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
  
## 请参阅  
 [函数调用](../c-language/function-calls.md)