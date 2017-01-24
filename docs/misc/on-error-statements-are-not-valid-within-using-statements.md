---
title: "“On Error”语句在“Using”语句内无效 | Microsoft Docs"
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
  - "vbc36013"
  - "bc36013"
helpviewer_keywords: 
  - "BC36013"
ms.assetid: 5b399bf9-6595-46e0-a808-378f6c28568b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “On Error”语句在“Using”语句内无效
`On Error` 语句出现在 `Using` 语句中，但在该上下文中无效。  
  
 **错误 ID：**BC36013  
  
### 更正此错误  
  
-   使用结构化的错误处理（如 `Try…Catch` 块）代替 `On Error` 语句。  
  
## 请参阅  
 [Visual Basic 的结构化异常处理概述](http://msdn.microsoft.com/zh-cn/bb81af80-a735-4873-9711-6151a48e418a)   
 [选择何时使用结构化和非结构化异常处理 \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/e897d7ca-07e8-45dd-8a6d-a5b2a2fc9b9a)   
 [On Error 语句](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)   
 [如何：在 Visual Basic 中对具有 Try…Catch 块的代码进行测试](http://msdn.microsoft.com/zh-cn/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)