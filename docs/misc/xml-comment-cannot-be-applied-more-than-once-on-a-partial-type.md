---
title: "XML 注释无法在一个分部 &lt;type&gt; 上应用多次 | Microsoft Docs"
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
  - "bc42314"
  - "vbc42314"
helpviewer_keywords: 
  - "BC42314"
ms.assetid: 23c76238-843a-44fe-88b7-25e604ee924b
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 注释无法在一个分部 &lt;type&gt; 上应用多次
XML 注释无法在一个分部 \<type\> 上应用多次。 将忽略此 \<type\> 的 XML 注释。  
  
 XML 注释块只能出现在分部类型的一部分上面。  
  
 如果 XML 注释块出现在分部类型的多个部分上面，则将为每个注释块创建此警告，并且将忽略顶级 XML 注释。  
  
 **错误 ID：**BC42314  
  
### 更正此错误  
  
-   删除冗余的注释块。  
  
## 请参阅  
 [如何：创建 XML 文档](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML 注释标记](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)