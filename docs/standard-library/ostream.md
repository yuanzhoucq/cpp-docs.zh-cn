---
title: "&lt;ostream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<ostream>"
  - "<ostream>"
  - "ostream/std::<ostream>"
  - "std::<ostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream 标头"
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;ostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义模板类 [basic\_ostream](../standard-library/basic-ostream-class.md)，此模板类可调解 iostreams 的插入。  此标头还定义了若干相关的操控程序。  （此标头通常包含在另一个 iostream 标头中。  很少会直接包含它。）  
  
## 语法  
  
```  
  
#include <ostream>  
  
```  
  
### Typedef  
  
|||  
|-|-|  
|[ostream](../Topic/ostream.md)|通过专用于 `char` 的 `basic_ostream` 和专用于 `char` 的 `char_traits` 创建类型。|  
|[wostream](../Topic/wostream.md)|通过专用于 `wchar_t` 的 `basic_ostream` 和专用于 `wchar_t` 的 `char_traits` 创建类型。|  
  
### 操控器  
  
|||  
|-|-|  
|[endl](../Topic/endl.md)|终止行并刷新缓冲区。|  
|[结尾](../Topic/ends%20\(Standard%20C++%20Library\).md)|终止字符串。|  
|[flush](../Topic/flush%20\(Standard%20C++%20Library\).md)|刷新缓冲区。|  
||将 `basic_ostream` 对象参数左侧的值与 `basic_ostream` 对象参数右侧的值进行交换。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 \<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md)|将各种类型写入流。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_ostream](../standard-library/basic-ostream-class.md)|模板类描述控制元素和编码对象插入到流缓存区中的对象。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)