---
title: "“&lt;说明符&gt;”在接口属性声明中无效 | Microsoft Docs"
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
  - "vbc30273"
  - "bc30273"
helpviewer_keywords: 
  - "BC30273"
ms.assetid: f10c4f5f-6176-4dba-99a9-b58f3b390fba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;说明符&gt;”在接口属性声明中无效
接口内的 `Property` 语句包含无效的关键字，如 `Implements`。 接口只能定义成员，而不能实现它们。  
  
 **错误 ID：**BC30273  
  
### 更正此错误  
  
-   从声明语句中删除无效的关键字。  
  
-   将接口成员的实现移动到实现该接口的类。  
  
## 请参阅  
 [Interface 语句](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements 语句](../Topic/Implements%20Statement.md)