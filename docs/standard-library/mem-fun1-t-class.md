---
title: "mem_fun1_t 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mem_fun1_t"
  - "std.mem_fun1_t"
  - "std::mem_fun1_t"
  - "xfunctional/std::mem_fun1_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun1_t 类"
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mem_fun1_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一个适配器类，它允许有一个参数的**non\_const**成员函数作为二元函数对象被调用，该一元函数初始化时有一个指针参数。  
  
## 语法  
  
```  
template<class Result, class Type, class Arg>  
   class mem_fun1_t : public binary_function<Type *, Arg, Result> {  
      explicit mem_fun1_t(  
         Result (Type::* _Pm )( Arg )   
         );  
      Result operator()(  
         Type* _Pleft,   
         Arg _Right  
         ) const;  
   };  
```  
  
#### 参数  
 `_Pm`  
 为类转换是 **类型** 的成员函数的指针到函数对象。  
  
 `_Pleft`  
 `_Pm` 对象成员函数调用。  
  
 `_Right`  
 为 `_Pm`的参数。  
  
## 返回值  
 可容纳的二进制函数。  
  
## 备注  
 类模板 `_Pm`存储副本，必须是指向类 **类型**的成员函数中，私有成员对象。  它定义了其成员函数 `operator()` 返回为 \(**\_Pleft**\-\>\* `_Pm`\)\(**\_Right**\)。  
  
## 示例  
 通常不直接使用 `mem_fun1_t` 构造函数；Helper 函数 `mem_fun` 来改写成员函数。  为有关如何参见 [mem\_fun](../Topic/mem_fun%20Function.md) 适配器使用成员函数。  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)