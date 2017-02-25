---
title: "NMAKE 错误 U1001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1001"
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 错误 U1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 宏中的非法字符“character”  
  
 给定字符出现在宏中，但它不是字母、数字或下划线。  
  
 此错误可能是由于宏展开中缺少冒号而造成的：  
  
```  
syntax error : illegal character '=' in macro  
```