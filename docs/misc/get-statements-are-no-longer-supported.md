---
title: "不再支持“Get”语句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30829"
  - "bc30829"
helpviewer_keywords: 
  - "BC30829"
ms.assetid: 8d798357-7efb-4423-9808-8b20777b97ba
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支持“Get”语句
不再支持 `Get` 语句。 文件 I\/O 功能在 `Microsoft.VisualBasic` 命名空间中可用。  
  
 文件操作不支持 `Get`，只能在属性过程语法中使用它。  
  
 **错误 ID：**BC30829  
  
### 更正此错误  
  
1.  使用 `System.IO`、`FileSystemObject`和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 运行时函数的成员执行文件操作。  
  
## 请参阅  
 [处理驱动器、目录和文件](../Topic/Processing%20Drives,%20Directories,%20and%20Files%20\(Visual%20Basic\).md)   
 [Get 语句](../Topic/Get%20Statement.md)   
 [使用 Visual Basic 访问文件](../Topic/File%20Access%20with%20Visual%20Basic.md)