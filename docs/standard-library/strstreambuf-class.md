---
title: "strstreambuf 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.strstreambuf"
  - "strstreambuf"
  - "std::strstreambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstreambuf 类"
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# strstreambuf 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一种流缓冲区，它对存储在 `char` 数组对象中的元素和元素序列之间的来回传输进行控制。  
  
## 语法  
  
```  
  
class strstreambuf : public streambuf  
  
```  
  
## 备注  
 可在必要时对它进行分配、扩展和释放以适应序列中的更改，具体取决于对象的构造方式。  
  
 类 `strstreambuf` 的对象将模式信息的几个位存储为其 `strstreambuf` 模式。 这些位指示受控序列是否：  
  
-   已分配且最后需要释放。  
  
-   是可修改的。  
  
-   可通过重新分配存储进行扩展。  
  
-   已被冻结并因此需要在对象被销毁前进行解冻，或者已由不是对象的某个代理释放（若已分配）。  
  
 无论这些单独模式位的状态如何，都不能修改或扩展已冻结的受控序列。  
  
 此对象还存储指向控制 `strstreambuf` 分配的两个函数的指针。 如果这些指针都是空指针，则对象会自行设计用于分配和释放受控序列存储的方法。  
  
> [!NOTE]
>  此类已弃用。 请考虑使用 [stringbuf](../Topic/stringbuf.md) 或 [wstringbuf](../Topic/wstringbuf.md) 相反。  
  
### 构造函数  
  
|||  
|-|-|  
|[strstreambuf](../Topic/strstreambuf::strstreambuf.md)|构造 `strstreambuf` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[freeze](../Topic/strstreambuf::freeze.md)|导致无法通过流缓冲区操作使用流缓冲区。|  
|[Overflow — 溢出](../Topic/strstreambuf::overflow.md)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|  
|[pbackfail](../Topic/strstreambuf::pbackfail.md)|一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。|  
|[pcount](../Topic/strstreambuf::pcount.md)|返回写入到受控序列的元素计数。|  
|[seekoff](../Topic/strstreambuf::seekoff.md)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|  
|[seekpos](../Topic/strstreambuf::seekpos.md)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|  
|[str](../Topic/strstreambuf::str.md)|调用 [freeze](../Topic/strstreambuf::freeze.md)，然后将返回指向受控序列开头的指针。|  
|[underflow](../Topic/strstreambuf::underflow.md)|一个受保护的虚拟函数，用于从输入流中提取当前元素。|  
  
## 要求  
 **标头：**\<strstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [streambuf](../Topic/streambuf.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)