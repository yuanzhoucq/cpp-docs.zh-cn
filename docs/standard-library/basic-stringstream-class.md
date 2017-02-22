---
title: "basic_stringstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_stringstream"
  - "basic_stringstream"
  - "std::basic_stringstream"
  - "sstream/std::basic_stringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringstream 类"
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# basic_stringstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述了一个对象，该对象可通过使用 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 类的流缓冲区控制元素和编码对象的插入和提取。  
  
## 语法  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### 参数  
 `Alloc`  
 分配器类。  
  
 `Elem`  
 字符串的基本元素的类型。  
  
 *Tr*  
 字符串的基本元素上专用的字符特征。  
  
## 备注  
 该模板类描述了一个对象，该对象可通过使用 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 类的流缓冲区控制元素和编码对象的插入和提取，其中 **Elem** 类型的元素的字符特征由类 **Tr** 确定，且其元素由类 `Alloc` 的分配器进行分配。  该对象存储 basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\> 类的对象。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_stringstream](../Topic/basic_stringstream::basic_stringstream.md)|构造 `basic_stringstream` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringstream::allocator_type.md)|类型是模板参数 `Alloc` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_stringstream::rdbuf.md)|将类型 `pointer` 的存储流缓冲区的地址返回到 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>。|  
|[str](../Topic/basic_stringstream::str.md)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|  
  
## 要求  
 **标头：**\<sstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)