---
title: "文本和二进制流 | Microsoft Docs"
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
  - "二进制流"
  - "文本流"
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 文本和二进制流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文本流包含可被写入一个面向文本显示的一个或多个文本行，以便可读取。  当从文本流读取数据时，程序在每行末读取 `NL` \(换行符\)。  在写入文本流时，程序写入 `NL` 表示行的结尾。  若要在文件文本的目标环境中匹配不同的约定，库函数在程序和文本流之间修改数字和已传送字符的表示。  
  
 因此，文本流中的定位是有限的。  通过调用 [fgetpos](../c-runtime-library/reference/fgetpos.md)或[ftell](../c-runtime-library/reference/ftell-ftelli64.md)获取当前文件位置指示器。  通过调用 [fsetpos](../c-runtime-library/reference/fsetpos.md) 或 [fseek](../c-runtime-library/reference/fseek-fseeki64.md)，在此位置或流的开始或结尾处确定文本流位置。  可能不支持其他位置的更改。  
  
 对于最大可移植，程序不应编写：  
  
-   空文件。  
  
-   行尾的空白字符。  
  
-   部分行 \(在文件尾省略 `NL`\)。  
  
-   除可打印字符、NL 和 `HT` \(横向制表符\) 之外的字符。  
  
 如果您遵循这些规则，创建文件时，从文本流读取字符的序列 \(字节还是作为多字节字符\) 将与要写入的文本流的字符学列匹配。  否则，当关闭时，如果文件为空，库函数删除刚创建的文件。  也可以修改或删除写入文件的字符。  
  
 二进制流包含一个或多个字节的任意信息。  可以将任意对象存储的值写入（按字节）二进制流，当写入时，恰好读取对象的值。  库函数不修改程序和二进制流之间传输的字节。  然而，可以追加任意个数的null字节到二进制流的文件中。  程序必须处理这些附加在任何二进制流的末尾的 null 字节。  
  
 因此，定位在一个二进制流被很好地定义,除了相对于流的末尾的定位。  与文本流相似，可以获取和修改当前文件位置指示符。  此外，[ftell](../c-runtime-library/reference/ftell-ftelli64.md) 和 [fseek](../c-runtime-library/reference/fseek-fseeki64.md) 使用从流开始的偏移量的计数，因此，对这些偏移的整型算法产生可预知的结果。  
  
 字节流将文件视作字节序列。  在程序中，除了上面描述的可能的变化，流类似于字节序列。  
  
## 请参阅  
 [文件和流](../c-runtime-library/files-and-streams.md)