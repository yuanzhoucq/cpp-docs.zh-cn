---
title: "fpos 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.fpos"
  - "std::fpos"
  - "iosfwd/std::fpos"
  - "fpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fpos 类"
  - "fpos 类, 关于 fpos 类"
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# fpos 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述了一个对象，该对象可以存储还原任何流内的任意文件位置指示器所需的全部信息。  fpos \<**St**\> 类的对象能够有效存储至少两个成员对象：  
  
-   一是 [streamoff](../Topic/streamoff.md) 类型的字节偏移。  
  
-   二是供 basic\_filebuf 类的对象使用的 **St** 类型的转换状态，通常为 `mbstate_t`。  
  
 它还能存储 `fpos_t` 类型的任意文件位置，以供 [basic\_filebuf](../standard-library/basic-filebuf-class.md) 类的对象使用。  但是，对于文件大小受限的环境，`streamoff` 和 `fpos_t` 有时可能互换使用。  对于不具有依赖于状态的编码的流的环境，实际上可能不会使用 `mbstate_t`。  因此，所存储成员对象的数目可能会有所不同。  
  
## 语法  
  
```  
  
     template <class   
     Statetype  
     >  
class fpos  
```  
  
#### 参数  
 *Statetype*  
 状态信息。  
  
### 构造函数  
  
|||  
|-|-|  
|[fpos](../Topic/fpos::fpos.md)|创建一个包含有关流中位置（偏移量）信息的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[seekpos](../Topic/fpos::seekpos.md)|仅由标准 C\+\+ 库内部使用。  请勿从代码中调用此方法。|  
|[state](../Topic/fpos::state.md)|设置或返回转换状态。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/fpos::operator!=.md)|测试文件位置指示器是否不相等。|  
|[运算符 \+](../Topic/fpos::operator+.md)|递增文件位置指示器。|  
|[运算符 \+\=](../Topic/fpos::operator+=.md)|递增文件位置指示器。|  
|[operator\-](../Topic/fpos::operator-.md)|递减文件位置指示器。|  
|[operator\-\=](../Topic/fpos::operator-=.md)|递减文件位置指示器。|  
|[operator\=\=](../Topic/fpos::operator==.md)|测试文件位置指示器是否相等。|  
|[operator streamoff](../Topic/fpos::operator%20streamoff.md)|将 `fpos` 类型的对象强制转换为 `streamoff` 类型的对象。|  
  
## 要求  
 **标头：**\<ios\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)