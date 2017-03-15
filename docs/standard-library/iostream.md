---
title: "&lt;iostream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<iostream>"
  - "std::<iostream>"
  - "<iostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iostream 标头"
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# &lt;iostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明控制从标准流读取和写入到标准流的对象。  这通常是从 C\+\+ 程序执行输入和输出需要包括的唯一标头。  
  
## 语法  
  
```  
  
#include <iostream>  
  
```  
  
## 备注  
 这些对象分为两组：  
  
-   [cin](../Topic/cin.md)、[cout](../Topic/cout.md)、[cerr](../Topic/cerr.md) 和 [clog](../Topic/clog.md) 面向字节，执行传统的每次一字节的传输。  
  
-   [wcin](../Topic/wcin.md)、[wcout](../Topic/wcout.md)、[wcerr](../Topic/wcerr.md) 和 [wclog](../Topic/wclog.md) 面向宽字节，与程序内部操作的宽字符相互转换。  
  
 一旦对流执行某些操作（例如标准输入），就不能对同一个流执行面向另一种字符的操作。  因此，程序无法对 [cin](../Topic/cin.md) 和 [wcin](../Topic/wcin.md) 等进行互换操作。  
  
 此标头中声明的所有对象共享一个特殊属性，可以假定在你定义的任意静态对象之前，将在包含 \<iostream\> 的翻译单元中构造这些对象。  同样，也可以假定在你定义任意此类静态对象的析构函数之前，这些对象不会受到破坏。  （但是，在程序终止过程中输出流将刷新。） 因此，可以在程序启动之前和程序终止之后安全地读取或写入标准流。  
  
 但这种保证并不普遍。  静态构造函数可能调用另一个翻译单元中的函数。  由于翻译单元在静态构造中的顺序不确定，因此被调用的函数不能假定已构造了此标头中声明的对象。  若要在此类上下文中使用这些对象，必须先构造 [ios\_base::Init](../Topic/ios_base::Init.md) 类的对象。  
  
### 全局流对象  
  
|||  
|-|-|  
|[cerr](../Topic/cerr.md)|指定 `cerr` 全局流。|  
|[cin](../Topic/cin.md)|指定 `cin` 全局流。|  
|[clog](../Topic/clog.md)|指定 `clog` 全局流。|  
|[cout](../Topic/cout.md)|指定 `cout` 全局流。|  
|[wcerr](../Topic/wcerr.md)|指定 `wcerr` 全局流。|  
|[wcin](../Topic/wcin.md)|指定 `wcin` 全局流。|  
|[wclog](../Topic/wclog.md)|指定 `wclog` 全局流。|  
|[wcout](../Topic/wcout.md)|指定 `wcout` 全局流。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)