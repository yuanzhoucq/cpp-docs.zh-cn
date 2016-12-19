---
title: "remove_volatile 类 | Microsoft Docs"
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
  - "std::tr1::remove_volatile"
  - "std.tr1.remove_volatile"
  - "remove_volatile"
  - "std.remove_volatile"
  - "std::remove_volatile"
  - "type_traits/std::remove_volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_volatile 类 [TR1]"
  - "remove_volatile"
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove_volatile 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从类型设置非可变类型。  
  
## 语法  
  
```  
template<class T>  
    struct remove_volatile;  
  
template<class T>  
  using remove_volatile_t = typename remove_volatile<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `remove_volatile<T>` 的实例保留修改后的类型，当 `T1` 为 `T` 形式时，此类型为 `volatile T1`，否则为 `T`。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_volatile_t<volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << " remove_volatile_t<volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_volatile\_t\<volatile int\> \=\= int**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_volatile 类](../standard-library/add-volatile-class.md)