---
title: "remove_reference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.remove_reference"
  - "std::tr1::remove_reference"
  - "remove_reference"
  - "std.remove_reference"
  - "std::remove_reference"
  - "type_traits/std::remove_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_reference 类 [TR1]"
  - "remove_reference"
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_reference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从类型设定非引用类型。  
  
## 语法  
  
```  
template<class T>  
    struct remove_reference;  
  
template<class T>  using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `remove_reference<T>` 的实例保留修改后的类型，当 `T1` 为 `T` 形式时，此类型为 `T1&`，否则为 `T`。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_lvalue\_reference 类](../standard-library/add-lvalue-reference-class.md)