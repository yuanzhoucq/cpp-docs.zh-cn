---
title: "错误 C1852 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1852"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1852"
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1852
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“filename”不是有效的预编译头文件  
  
 文件不是预编译头文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  使用 **\/Yu** 或 **\#pragma hdrstop** 指定的无效文件。  
  
2.  如果未另行指定，编译器将假定 .pch 为文件扩展名。