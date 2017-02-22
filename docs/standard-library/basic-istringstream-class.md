---
title: "basic_istringstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_istringstream"
  - "sstream/std::basic_istringstream"
  - "basic_istringstream"
  - "std.basic_istringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istringstream 类"
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# basic_istringstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述了一个对象，该对象控制从 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 类的流缓冲区中提取元素和编码对象的操作。  
  
## 语法  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_istringstream : public basic_istream<Elem, Tr>  
```  
  
#### 参数  
 `Alloc`  
 分配器类。  
  
 `Elem`  
 字符串的基本元素的类型。  
  
 *Tr*  
 字符串的基本元素上专用的字符特征。  
  
## 备注  
 该模板类描述一个对象，该对象控制从[basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 类的流缓冲区中提取元素和编码对象的操作，该类具有 **Elem** 类型的元素，元素的字符特征由 **Tr** 类决定，并且其元素由 `Alloc` 类 的分配器进行分配。  该对象存储 basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\> 类的对象。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_istringstream](../Topic/basic_istringstream::basic_istringstream.md)|构造 `basic_istringstream` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_istringstream::allocator_type.md)|类型是模板参数 `Alloc` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_istringstream::rdbuf.md)|将 `pointer` 类型的存储流缓冲区的地址返回到 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>。|  
|[str](../Topic/basic_istringstream::str.md)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|  
|[swap](../Topic/basic_istringstream::swap.md)|将此 `basic_istringstream` 对象中的值与所提供对象的值进行交换。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/basic_istringstream::operator=.md)|将值从对象参数赋给此 `basic_istringstream` 对象。|  
  
## 要求  
 **标头：**\<sstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)