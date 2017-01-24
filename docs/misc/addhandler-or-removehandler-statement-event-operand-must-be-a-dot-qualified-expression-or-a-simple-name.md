---
title: "“AddHandler”或“RemoveHandler”语句事件操作数必须是以点限定的表达式或者是简单的名称。 | Microsoft Docs"
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
  - "vbc30677"
  - "bc30677"
helpviewer_keywords: 
  - "BC30677"
ms.assetid: b71eb2f0-0bb2-4aeb-94ec-5c37ab960d9e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “AddHandler”或“RemoveHandler”语句事件操作数必须是以点限定的表达式或者是简单的名称。
为 `AddHandler` 或 `RemoveHandler` 的事件参数指定的项未被识别为事件。  
  
 **错误 ID：**BC30677  
  
### 更正此错误  
  
-   指定引发事件的对象名称，后跟点 \(`.`\) 和事件名称，如以下示例所示。  
  
     [!code-vb[VbVbalrEventError#30](../misc/codesnippet/VisualBasic/addhandler-or-removehandler-statement-event-operand-must-be-a-dot-qualified-expression-or-a-simple-name_1.vb)]  
  
## 请参阅  
 [AddHandler 语句](../Topic/AddHandler%20Statement.md)   
 [RemoveHandler 语句](../Topic/RemoveHandler%20Statement.md)   
 [不在生成中：AddHandler 和 RemoveHandler](http://msdn.microsoft.com/zh-cn/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)