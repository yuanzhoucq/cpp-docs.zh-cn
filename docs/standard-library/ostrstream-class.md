---
title: "ostrstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.oststream"
  - "oststream"
  - "std::oststream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostrstream 类"
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# ostrstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述控制元素插入的对象，并将对象编码到 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中。  
  
## 语法  
  
```  
  
class ostrstream : public ostream  
  
```  
  
## 备注  
 该对象存储 `strstreambuf` 类的对象。  
  
> [!NOTE]
>  此类已弃用。  请考虑使用 [ostringstream](../Topic/ostringstream.md) 或 [wostringstream](../Topic/wostringstream.md) 作为替代。  
  
### 构造函数  
  
|||  
|-|-|  
|[ostrstream](../Topic/ostrstream::ostrstream.md)|构造 `ostrstream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[freeze](../Topic/ostrstream::freeze.md)|导致无法通过流缓冲区操作使用流缓冲区。|  
|[pcount](../Topic/ostrstream::pcount.md)|返回写入到受控序列的元素计数。|  
|[rdbuf](../Topic/ostrstream::rdbuf.md)|返回指向流的关联 `strstreambuf` 对象的指针。|  
|[str](../Topic/ostrstream::str.md)|调用 [freeze](../Topic/strstreambuf::freeze.md)，然后将返回指向受控序列开头的指针。|  
  
## 要求  
 **标头：**\<strstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [ostream](../Topic/ostream.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)