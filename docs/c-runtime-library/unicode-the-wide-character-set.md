---
title: "Unicode：宽字符集 | Microsoft Docs"
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
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "Unicode [C++], 宽字符集"
  - "宽字符 [C++], Unicode"
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Unicode：宽字符集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宽字符是双字节多语言字符代码。  在当今的全球计算业内使用的任何使用的字符（包括技术符号和特殊的发布字符），都可以根据 Unicode 规范表示为宽字符形式。  由包括 Microsoft 在内的大型财团开发和维护，Unicode 标准现在被广泛接受。  
  
 宽字符是 `wchar_t`类型。  宽字符字符串表示为一个`wchar_t[]` 数组并由`wchar_t*` 指针指向它。  你可以通过字母`L`作为字符的前缀将任何ASCII字符表示为宽字符形式。  例如, L'\\0' 是终止宽（16位） `NULL` 字符。  同样，你可以通过用字母 L 作为 ASCII 字符串的前缀 \(L"Hello"\) 将任何 ASCII 字符串表示为宽字符字符串形式。  
  
 通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。  另外，在多字节编码中一次只能表示一个区域设置，而世界上的所有字符集都同时以 Unicode 表示形式表示。  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)