---
title: "带符号的按位运算 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "按位运算"
  - "带符号的按位运算"
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 带符号的按位运算
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3** 对带符号整数进行的按位运算的结果  
  
 对带符号整数进行的按位运算的工作方式与对无符号整数进行的按位运算的工作方式相同。  例如，`–16 & 99` 可用二进制格式表示  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 按位“与”的结果为 96。  
  
## 请参阅  
 [整数](../c-language/integers.md)