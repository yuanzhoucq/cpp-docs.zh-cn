---
title: "mem_fun_t 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mem_fun_t"
  - "xfunctional/std::mem_fun_t"
  - "std::mem_fun_t"
  - "std.mem_fun_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun_t 类"
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# mem_fun_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一个适配器类，它允许一个没有参数的**non\_const**成员函数作为一元函数对象被调用，该一元函数初始化时有一个指针参数。  
  
## 语法  
  
```  
template<class Result, class Type>  
   class mem_fun_t : public unary_function<Type *, Result> {  
      explicit mem_fun_t(Result ( Type::*_Pm )( ) );  
      Result operator()( Type* _Pleft ) const;  
   };  
```  
  
#### 参数  
 `_Pm`  
 为类转换是 **类型** 的成员函数的指针到函数对象。  
  
 `_Pleft`  
 `_Pm` 对象成员函数调用。  
  
## 返回值  
 一个可以满足的一元函数。  
  
## 备注  
 类模板 `_Pm`存储副本，必须是指向类 **类型**的成员函数中，私有成员对象。  它定义了其成员函数为 `operator()` 返回 \(\*`_Pleft`\-\>`_Pm`\) \(\)。  
  
## 示例  
 通常不直接使用 `mem_fun_t` 构造函数；Helper 函数 `mem_fun` 来改写成员函数。  为有关如何参见 [mem\_fun](../Topic/mem_fun%20Function.md) 适配器使用成员函数。  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<functional\>](../standard-library/functional.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)