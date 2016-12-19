---
title: "&lt; &gt; istream | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istream/std::<istream>"
  - "std.<istream>"
  - "<istream>"
  - "std::<istream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream 标头"
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: 20
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; &gt; istream
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义调解 iostreams 提取的模板类 basic\_istream，以及调解插入和提取的模板类 basic\_iostream。 标头还定义了一个相关的操控程序。 通常会由另一个 iostreams 标头为你包括此头文件；几乎不需要直接包括它。  
  
## 语法  
  
```  
  
#include <istream>  
  
```  
  
### Typedef  
  
|||  
|-|-|  
|[iostream](../Topic/iostream.md)|专用于 `char` 的类型 `basic_iostream`。|  
|[istream](../Topic/istream.md)|专用于 `char` 的类型 `basic_istream`。|  
|[wiostream](../Topic/wiostream.md)|专用于 **wchar** 的类型 `basic_iostream`。|  
|[wistream](../Topic/wistream.md)|专用于 **wchar** 的类型 `basic_istream`。|  
  
### 操控器  
  
|||  
|-|-|  
|[ws](../Topic/ws.md)|跳过流中的空白。|  
|[swap](../Topic/%3Cistream%3E%20swap.md)|交换两个流对象。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md)|从流中提取字符和字符串。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_iostream](../standard-library/basic-iostream-class.md)|可以完成输入和输出的流类。|  
|[basic\_istream](../standard-library/basic-istream-class.md)|该模板类描述一个控制从流缓冲区提取元素和编码对象的对象（其字符特征由类 **Tr** 确定，也称为 [traits\_type](../Topic/basic_ios::traits_type.md)），该流缓冲区具有 **Elem** 类型的元素（也称为 [char\_type](../Topic/basic_ios::char_type.md)）。|  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)