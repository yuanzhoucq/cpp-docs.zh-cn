---
title: "&lt;fstream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<fstream>"
  - "<fstream>"
  - "std.<fstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fstream 标头"
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;fstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义若干类，这些类支持在存储于外部文件中的序列上的 iostreams 操作。  
  
## 语法  
  
```  
  
#include <fstream>  
  
```  
  
### Typedef  
  
|||  
|-|-|  
|[filebuf](../Topic/filebuf.md)|专用于 `char` 模板参数的类型 `basic_filebuf`。|  
|[fstream](../Topic/fstream.md)|专用于 `char` 模板参数的类型 `basic_fstream`。|  
|[ifstream](../Topic/ifstream.md)|专用于 `char` 模板参数的类型 `basic_ifstream`。|  
|[ofstream](../Topic/ofstream.md)|专用于 `char` 模板参数的类型 `basic_ofstream`。|  
|[wfstream](../Topic/wfstream.md)|专用于 `wchar_t` 模板参数的类型 `basic_fstream`。|  
|[wifstream](../Topic/wifstream.md)|专用于 `wchar_t` 模板参数的类型 `basic_ifstream`。|  
|[wofstream](../Topic/wofstream.md)|专用于 `wchar_t` 模板参数的类型 `basic_ofstream`。|  
|[wfilebuf](../Topic/wfilebuf.md)|专用于 `wchar_t` 模板参数的类型 `basic_filebuf`。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_filebuf](../standard-library/basic-filebuf-class.md)|该模板类描述对 **Elem** 类型的元素（其字符特征由类 **Tr** 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。|  
|[basic\_fstream](../standard-library/basic-fstream-class.md)|该模板类描述一个对象，该对象使用 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 类的流缓冲区控制元素和编码对象的插入和提取，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
|[basic\_ifstream](../standard-library/basic-ifstream-class.md)|该模板类描述一个对象，该对象控制从 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 类的流缓冲区提取元素和编码对象，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
|[basic\_ofstream](../standard-library/basic-ofstream-class.md)|该模板类描述一个对象，该对象控制向 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 类的流缓冲区插入元素和编码对象，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)