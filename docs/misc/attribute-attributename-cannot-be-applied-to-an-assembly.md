---
title: "特性“&lt;attributename&gt;”不能应用于程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30548"
  - "vbc30548"
helpviewer_keywords: 
  - "BC30548"
ms.assetid: bc36f094-626a-4907-b80b-f195155fa5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 特性“&lt;attributename&gt;”不能应用于程序集
试图将特性应用于某个程序集，该程序集的 `AttributeUsageAttribute` 未指定 `AttributeTargets.Assembly`。 声明该特性时，未定义其适用于程序集。  
  
 **错误 ID：**BC30548  
  
### 更正此错误  
  
1.  检查特性声明，并指定 `AttributeTargets.Assembly` 或 `AttributeTargets.All`。  
  
## 请参阅  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>