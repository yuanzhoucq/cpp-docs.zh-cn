---
title: "输入/输出流 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "I/O [C++], 流"
  - "流 I/O"
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 输入/输出流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`basic_iostream`，请在头文件 \<istream\>定义，为处理输入和输出基于字符的 I\/O 流对象的类模板。  
  
 定义了 `basic_iostream` 字符的专用化，并且有助于使代码更易于阅读的 typedef 两个：`iostream` \(与混淆\) \<iostream\>头文件不是基于 `basic_iostream<char>`的 I\/O 流；`wiostream` 是基于 `basic_iostream<wchar_t>`的 I\/O 流。  
  
 有关更多信息，请参见[basic\_iostream 类](../standard-library/basic-iostream-class.md)、[iostream](../Topic/iostream.md)和[wiostream](../Topic/wiostream.md)。  
  
 从 `basic_iostream` 派生在类模板 `basic_fstream`，用于定义来回转换字符数据文件流。  
  
 还提供 `basic_fstream`的特定字符专用化的 typedef。  它们是 `fstream`，该文件 I\/O 流基于 `char`和 `wfstream`，该文件 I\/O 流基于 `wchar_t`。  有关更多信息，请参见[basic\_fstream 类](../standard-library/basic-fstream-class.md)、[fstream](../Topic/fstream.md)和[wfstream](../Topic/wfstream.md)。  使用这些 typedef 需要单独的头文件 \<fstream\>。  
  
> [!NOTE]
>  尽管 `basic_fstream` 对象用于执行文件 I\/O 时，但基础包含缓冲区读取和写入的分别指定的位置，即当前输入和输出当前位置。附加，另外，读取某些数据将输出位置。  
  
 类模板 `basic_stringstream` 及其常用时，`stringstream`，通常与 I\/O 流对象 \(使用 INSERT 和提取字符数据。  有关详细信息，请参阅[basic\_stringstream 类](../standard-library/basic-stringstream-class.md)。  
  
## 请参阅  
 [stringstream](../Topic/stringstream.md)   
 [basic\_stringstream 类](../standard-library/basic-stringstream-class.md)   
 [\<sstream\>](../standard-library/sstream.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)