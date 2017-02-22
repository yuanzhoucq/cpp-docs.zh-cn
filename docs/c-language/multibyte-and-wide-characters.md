---
title: "多字节和宽字符 | Microsoft Docs"
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
  - "字符代码 [C++], 多字节"
  - "字符代码 [C++], 宽"
  - "字符数据类型 [C]"
  - "字符 [C++], 代码"
  - "字符 [C++], 宽"
  - "全球化 [C++], 字符集"
  - "国际应用程序 [C++], 字符显示"
  - "多字节字符 [C++]"
  - "类型 [C], 字符"
  - "Unicode [C++], 宽字符集"
  - "宽字符 [C++]"
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 多字节和宽字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多字节字符是由一个或多个字节的序列构成的字符。  每个字节序列表示扩展字符集中的单个字符。  多字节字符用于字符集（如日文汉字）中。  
  
 宽字符是宽度始终为 16 位的多语言字符代码。  字符常量的类型是 `char`；对于宽字符，该类型是 `wchar_t`。  由于宽字符始终具有固定大小，因此使用宽字符集可以简化使用国际字符集进行的编程。  
  
 宽字符串文本 `L"hello"` 将成为类型为 `wchar_t` 的六个整数的数组。  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 Unicode 规范是宽字符的规范。  用于多字节和宽字符之间的转换的运行库例程包括 `mbstowcs`、`mbtowc`、`wcstombs` 和 `wctomb`。  
  
## 请参阅  
 [C 标识符](../c-language/c-identifiers.md)