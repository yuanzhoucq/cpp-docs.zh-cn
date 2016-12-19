---
title: "字节和宽流 | Microsoft Docs"
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
  - "Byte and Wide Streams"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字节流"
  - "宽流"
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字节和宽流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

字节流将文件视作字节序列。  在程序中，流与字节序列是相同的。  
  
 相反，宽流将文件视作多字节字符的序列，可以具有丰富多样的编码规则。\(如之前描述的，文本和二进制文件仍然被读取和写入。\)在程序中，流类似于对应宽字符的相对应序列。  在标准 C 库内两种表示形式之间的转换。  大体上，转换规则通过修改类别 `LC_CTYPE` 调用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 被改变。  每宽流确定其转换规则，当它变成面向宽，并会保留这些规则，即使 随后更改 `LC_CTYPE` 类别。  
  
 在宽流中定位遭受对于文本流相同的限制。  此外，文件位置指示符可能要面对的一个状态依赖编码。  通常，它包括流中字节偏移量和 `mbstate_t`类型的对象。  因此，唯一可靠的方式获取宽流中的文件的位置是通过调用 [fgetpos](../c-runtime-library/reference/fgetpos.md)，并且，唯一可靠的方法还原位置获得此方法是通过调用 [fsetpos](../c-runtime-library/reference/fsetpos.md)。  
  
## 请参阅  
 [文件和流](../c-runtime-library/files-and-streams.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)