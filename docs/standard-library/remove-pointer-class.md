---
title: "remove_pointer 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "remove_pointer"
  - "std.tr1.remove_pointer"
  - "std::tr1::remove_pointer"
  - "std.remove_pointer"
  - "std::remove_pointer"
  - "type_traits/std::remove_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_pointer 类 [TR1]"
  - "remove_pointer"
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_pointer 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从指向类型的指针设定类型。  
  
## 语法  
  
```  
template<class T>  
    struct remove_pointer;  
  
template<class T>  
  using remove_pointer_t = typename remove_pointer<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `remove_pointer<T>` 的实例保留修改后的类型，当 `T1` 为 `T`、`T1*`、`T1* const` 或 `T1* volatile` 形式时，此类型为 `T1* const volatile`，否则为 `T`。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_pointer_t<int *> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_pointer_t<int *> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_pointer\_t\<int \*\> \=\= int**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_pointer 类](../standard-library/add-pointer-class.md)