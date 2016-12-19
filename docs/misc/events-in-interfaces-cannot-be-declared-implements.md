---
title: "接口中的事件不能声明为“&lt;implements&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30688"
  - "vbc30688"
helpviewer_keywords: 
  - "BC30688"
ms.assetid: 577823c1-815c-4f1c-9177-4bbf73fa92db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 接口中的事件不能声明为“&lt;implements&gt;”
在接口中声明的事件不能实现其他接口的事件。  
  
 **错误 ID：**BC30688  
  
### 更正此错误  
  
1.  删除 `Implements` 语句。  
  
2.  实现类或结构中的事件。  
  
## 请参阅  
 [Interface 语句](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)