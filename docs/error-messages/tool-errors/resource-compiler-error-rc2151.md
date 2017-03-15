---
title: "资源编译器错误 RC2151 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2151"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2151"
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RC2151
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法重用字符串常数  
  
 在 **STRINGTABLE** 语句中您正在将同一个值使用两次。  确保您没有混合重叠十进制数值和十六进制数值。  
  
 **STRINGTABLE** 中的每个 ID 都必须是唯一的。  为取得最大效率，请使用从 16 的倍数开始的连续常数。