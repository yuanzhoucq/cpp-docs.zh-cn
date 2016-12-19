---
title: "&lt; &gt; streambuf | Microsoft Docs"
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
  - "std::<streambuf>"
  - "<streambuf>"
  - "streambuf/std::<streambuf>"
  - "std.<streambuf>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "streambuf 标头"
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; &gt; streambuf
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 iostreams 标准标头 \< streambuf \> 来定义此模板类 [basic\_streambuf](../standard-library/basic-streambuf-class.md)，这是 iostreams 类的基本操作。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。  
  
## 语法  
  
```  
  
#include <streambuf>  
  
```  
  
### Typedef  
  
|||  
|-|-|  
|[streambuf](../Topic/streambuf.md)|专用化使用 `char` 作为模板参数的 `basic_streambuf`。|  
|[wstreambuf](../Topic/wstreambuf.md)|专用化使用 `wchar_t` 作为模板参数的 `basic_streambuf`。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_streambuf 类](http://msdn.microsoft.com/zh-cn/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|此模板类描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)