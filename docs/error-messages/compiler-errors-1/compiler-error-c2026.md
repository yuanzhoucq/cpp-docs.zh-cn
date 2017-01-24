---
title: "编译器错误 C2026 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2026"
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字符串太大，已截断尾部字符  
  
 该字符串的长度超过了 16380 个单字节字符的限制。  
  
 在连接相邻字符串之前，字符串的长度不能超过 16380 个单字节字符。  
  
 大约为此长度的一半的 Unicode 字符串也会生成此错误。  
  
 如果某个字符串按如下定义，则会生成 C2026：  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 可以按如下所示对其进行分解：  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 可能需要在自定义资源或外部文件中存储异常大的字符串（32K 或更大）。  有关更多信息，请参见[创建新的自定义资源或数据资源](../../mfc/creating-a-new-custom-or-data-resource.md)。