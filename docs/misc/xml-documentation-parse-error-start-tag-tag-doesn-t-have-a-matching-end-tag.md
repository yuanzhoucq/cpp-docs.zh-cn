---
title: "XML 文档分析错误：开始标记“&lt;tag&gt;”没有匹配的结束标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42316"
  - "BC42316"
helpviewer_keywords: 
  - "BC42316"
ms.assetid: 45b68176-ebf6-43af-820e-6801aabb6c57
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 文档分析错误：开始标记“&lt;tag&gt;”没有匹配的结束标记
XML 文档分析错误：开始标记 \<tag\> 没有匹配的结束标记。 将忽略 XML 注释。  
  
 XML 注释包含开始标记，但不包含匹配的结束标记。  
  
 **错误 ID：**BC42316  
  
### 更正此错误  
  
-   添加与开始标记相匹配的结束标记。  
  
     — 或 —  
  
-   如果该标记不包含内部文本（如 [\<seealso\>](../Topic/%3Cseealso%3E%20\(Visual%20Basic\).md)），则在右尖括号前面指定一个正斜杠。  
  
## 请参阅  
 [XML 注释标记](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)   
 [使用 XML 将代码文档化](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)