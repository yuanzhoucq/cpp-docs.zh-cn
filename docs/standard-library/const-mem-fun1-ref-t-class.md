---
title: "const_mem_fun1_ref_t 类 | Microsoft Docs"
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
  - "std::const_mem_fun1_ref_t"
  - "std.const_mem_fun1_ref_t"
  - "xfunctional/std::const_mem_fun1_ref_t"
  - "const_mem_fun1_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_mem_fun1_ref_t 类"
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# const_mem_fun1_ref_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允许 **const** 成员函数采用作为二进制函数将调用对象的单个参数，将初始化具有引用参数的适配器类。  
  
## 语法  
  
```  
template<class Result, class Type, class Arg>  
   class const_mem_fun1_ref_t  
      : public binary_function<Type, Arg, Result> {  
   explicit const_mem_fun1_ref_t( Result (Type::*_Pm )( Arg ) const );  
   Result operator()(  
      const Type& _Left,  
      Arg _Right  
   ) const;  
   };  
```  
  
#### 参数  
 `_Pm`  
 为类转换是 **类型** 的成员函数的指针到函数对象。  
  
 `_Left`  
 **const** 对象的 `_Pm` 成员函数调用。  
  
 `_Right`  
 为 `_Pm`的参数。  
  
## 返回值  
 可容纳的二进制函数。  
  
## 备注  
 类模板 `_Pm`存储副本，必须是指向类 **类型**的成员函数中，私有成员对象。  它定义了其成员函数为 \( `operator()` 返回`_Left`。\* *\_Pm*\)`_Right`\( **const**\)。  
  
## 示例  
 通常不直接使用 `const_mem_fun1_ref_t` 构造函数；Helper 函数 `mem_fun_ref` 来改写成员函数。  参见 [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) 说明如何使用这些成员函数适配器作为示例。  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)