---
title: "pointer_to_binary_function 类 | Microsoft Docs"
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
  - "std::pointer_to_binary_function"
  - "xfunctional/std::pointer_to_binary_function"
  - "pointer_to_binary_function"
  - "std.pointer_to_binary_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_to_binary_function 类"
  - "pointer_to_binary_function 函数"
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointer_to_binary_function 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将二元函数指针转换为灵活的二元函数。  
  
## 语法  
  
```  
template<class Arg1, class Arg2, class Result>  
   class pointer_to_binary_function   
   : public binary_function <Arg1, Arg2, Result>   
   {  
   public:  
   explicit pointer_to_binary_function(  
      Result (*_pfunc )( Arg1, Arg2 )   
   );  
   Result operator()(  
      Arg1 _Left,   
      Arg2 _Right  
   ) const;  
   };  
```  
  
#### 参数  
 `_pfunc`  
 将二进制转换的函数。  
  
 `_Left`  
 左侧的对象 *\*\_pfunc* 调用。  
  
 `_Right`  
 正确的对象 *\*\_pfunc* 调用。  
  
## 返回值  
 模板类存储 **\_pfunc**副本。  它定义了其成员函数 `operator()` 返回**\_pfunc**\(\_Left 为 \(\*\)，\_Right\)。  
  
## 备注  
 binary 函数指针是函数对象，并可以传递到需要二进制函数作为参数的标准模板库 \(STL\) 算法，但它是不可靠的。  若要将它与一个适配器，例如绑定值。它或将它与非，必须为其提供使这满足成为可能的嵌套类型 **first\_argument\_type**、**second\_argument\_type**和 **result\_type**。  由 `pointer_to_binary_function` 的转换函数允许与适配器二进制函数指针\)。  
  
## 示例  
 直接很少使用 `pointer_to_binary_function` 构造函数。  为有关如何参见帮助程序函数 [ptr\_fun](../Topic/ptr_fun%20Function.md) 声明和使用 `pointer_to_binary_function` 适配器谓词。  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)