---
title: "“WriteOnly”属性必须提供“Set” | Microsoft Docs"
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
  - "bc30125"
  - "vbc30125"
helpviewer_keywords: 
  - "BC30125"
ms.assetid: c2b18086-9cd9-4094-b9a9-491c8d617096
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “WriteOnly”属性必须提供“Set”
如果某个属性声明为 `WriteOnly`，则它必须提供用于写入其值的过程。  
  
 **错误 ID：**BC30125  
  
### 更正此错误  
  
1.  请确保 `Property` 语句和 `End Property` 语句之间包含 `Set` 过程。  
  
2.  验证 `Property` 声明中的其他过程是否正确终止。  
  
## 请参阅  
 [Property 语句](../Topic/Property%20Statement.md)   
 [Set 语句](../Topic/Set%20Statement%20\(Visual%20Basic\).md)