---
title: "iterator 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator"
  - "std::iterator"
  - "std.iterator"
  - "xutility/std::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator 类"
  - "iterator 结构"
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# iterator 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于的空结构基本确保一个用户定义的迭代器类正确使用 **iterator\_trait**\(.\)。  
  
## 语法  
  
```  
template<class Category, class Type, class Distance = ptrdiff_t  
    class Pointer = Type*, class Reference = Type&>  
    struct iterator {  
        typedef Category iterator_category;  
        typedef Type value_type;  
        typedef Distance difference_type;  
        typedef Distance distance_type;  
        typedef Pointer pointer;  
        typedef Reference reference;  
    };  
```  
  
## 备注  
 模板结构用作基类型。对于所有迭代器。  它定义类型成员  
  
-   `iterator_category` \(模板参数的 `Category`\) 的同义词。  
  
-   `value_type` \(模板参数的同义词 **类型**\)。  
  
-   `difference_type` \(模板参数的 `Distance`\) 的同义词。  
  
-   模板参数的同义词`distance_type` \( `Distance`\)  
  
-   `pointer` \(模板参数的 `Pointer`\) 的同义词。  
  
-   `reference` \(模板参数的 `Reference`\) 的同义词。  
  
 请注意 `value_type` 不应为常数类型常量，即使在 **类型** 和引用对象的 **指针** 点指定常数 **类型**对象。  
  
## 示例  
 为有关如何参见 [iterator\_traits](../standard-library/iterator-traits-struct.md) 声明和使用类型在迭代器的基类。  
  
## 要求  
 **页眉：**\<迭代器\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)