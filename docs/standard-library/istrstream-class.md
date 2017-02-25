---
title: "istrstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istrstream"
  - "std::istrstream"
  - "std.istrstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istrstream 类"
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# istrstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述了一种对象，它对从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象的操作进行控制。  
  
## 语法  
  
```  
  
class istrstream : public istream  
  
```  
  
## 备注  
 该对象存储 `strstreambuf` 类的对象。  
  
> [!NOTE]
>  此类已弃用。 请考虑使用 [istringstream](../Topic/istringstream.md) 或 [wistringstream](../Topic/wistringstream.md) 相反。  
  
### 构造函数  
  
|||  
|-|-|  
|[istrstream](../Topic/istrstream::istrstream.md)|构造 `istrstream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[rdbuf](../Topic/istrstream::rdbuf.md)|返回指向流的关联 `strstreambuf` 对象的指针。|  
|[str](../Topic/istrstream::str.md)|调用 [freeze](../Topic/strstreambuf::freeze.md)，然后将返回指向受控序列开头的指针。|  
  
## 要求  
 **标头：**\<strstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [istream](../Topic/istream.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)