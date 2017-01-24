---
title: "元素名称不能使用“xmlns”前缀 | Microsoft Docs"
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
  - "vbc31189"
  - "bc31189"
helpviewer_keywords: 
  - "BC31189"
ms.assetid: 88716bb5-6766-4180-b2ed-1d1bee0ff7a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 元素名称不能使用“xmlns”前缀
使用 `xmlns` XML 命名空间前缀指定了 XML 元素文本。 例如:  
  
```vb#  
Dim elem = <xmlns:ElementName>  
```  
  
 XML 1.0 规范将 `xmlns` 标识为保留字。  
  
 **错误 ID：**BC31189  
  
### 更正此错误  
  
-   将 XML 命名空间前缀更改为有效值，或删除该前缀。  
  
## 请参阅  
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [Imports 语句（XML 命名空间）](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)