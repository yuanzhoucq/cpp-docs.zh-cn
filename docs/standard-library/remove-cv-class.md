---
title: "remove_cv 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "remove_cv"
  - "std::tr1::remove_cv"
  - "std.tr1.remove_cv"
  - "std.remove_cv"
  - "std::remove_cv"
  - "type_traits/std::remove_cv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_cv 类 [TR1]"
  - "remove_cv"
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_cv 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从类型设置非常量\/可变类型。  
  
## 语法  
  
```  
template<class T>  
    struct remove_cv;  
  
template<class T>  
  using remove_cv_t = typename remove_cv<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `remove_cv<T>` 的实例保留修改后的类型，当 `T` 为 `const T1`、`volatile T1` 或 `const volatile T1` 形式时，此类型为 `T1`，否则为 `T`。  
  
## 示例  
  
```  
  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_cv_t<const volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_cv_t<const volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_cv\_t\<const volatile int\> \=\= int**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_const 类](../standard-library/remove-const-class.md)   
 [remove\_volatile 类](../standard-library/remove-volatile-class.md)