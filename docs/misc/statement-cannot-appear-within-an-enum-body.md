---
title: "语句不能出现在枚举体内 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30619"
  - "bc30619"
helpviewer_keywords: 
  - "BC30619"
ms.assetid: 5d91d601-2a2d-418c-ae26-791d14a6f3cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 语句不能出现在枚举体内
语句不能出现在枚举体内。 假定已到达枚举末尾。  
  
 遇到意外的语言构造。 假定缺少 `End Enum` 构造，而且此点后的所有源代码都在枚举外。  
  
 **错误 ID：**BC30619  
  
### 更正此错误  
  
1.  验证枚举中所用代码的语法是否正确。  
  
2.  确保接口定义以 `End Enum` 构造结束。  
  
## 请参阅  
 [Enum 语句](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)