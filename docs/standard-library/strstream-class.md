---
title: "strstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::strstream"
  - "strstream"
  - "std.strstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstream 类"
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# strstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述了一个对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。  
  
## 语法  
  
```  
  
class strstream : public iostream  
  
```  
  
## 备注  
 该对象存储 `strstreambuf` 类的对象。  
  
> [!NOTE]
>  此类已弃用。  请考虑改用 [stringstream](../Topic/stringstream.md) 或 [wstringstream](../Topic/wstringstream.md)。  
  
### 构造函数  
  
|||  
|-|-|  
|[strstream](../Topic/strstream::strstream.md)|构造 `strstream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[freeze](../Topic/strstream::freeze.md)|导致无法通过流缓冲区操作使用流缓冲区。|  
|[pcount](../Topic/strstream::pcount.md)|返回写入到受控序列的元素计数。|  
|[rdbuf](../Topic/strstream::rdbuf.md)|返回指向流的关联 `strstreambuf` 对象的指针。|  
|[str](../Topic/strstream::str.md)|调用 [freeze](../Topic/strstreambuf::freeze.md)，然后将返回指向受控序列开头的指针。|  
  
## 要求  
 **标头：**\<strstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [iostream](../Topic/iostream.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)