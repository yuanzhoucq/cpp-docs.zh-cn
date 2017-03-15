---
title: "allocator&lt;void&gt; 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator<void>"
  - "std::allocator<void>"
  - "std.allocator<void>"
  - "allocator<void>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator<void> 类"
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# allocator&lt;void&gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

键入 `void`的模板类分配程序的专用化，定义此上下文有意义的类型。  
  
## 语法  
  
```  
template<>  
   class allocator<void> {  
   typedef void *pointer;  
   typedef const void *const_pointer;  
   typedef void value_type;  
   template<class Other>  
      struct rebind;  
   allocator( );  
   allocator(  
      const allocator<void>&  
   );  
   template<class Other>  
      allocator(  
         const allocator<Other>&  
      );  
   template<class Other>  
      allocator<void>& operator=(  
         const allocator<Other>&  
      );  
   };  
```  
  
## 备注  
 类显式专用化类型  [allocator](../standard-library/allocator-class.md) 模板类 *无效。*其构造函数和赋值运算符相同的行为。模板类的，但是，这仅定义以下类型：  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md)。  
  
-   [指针](../Topic/allocator::pointer.md)。  
  
-   [value\_type](../Topic/allocator::value_type.md)。  
  
-   [重新绑定](../Topic/allocator::rebind.md)，嵌套的模板类。  
  
## 要求  
 **页眉：**\<内存\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)