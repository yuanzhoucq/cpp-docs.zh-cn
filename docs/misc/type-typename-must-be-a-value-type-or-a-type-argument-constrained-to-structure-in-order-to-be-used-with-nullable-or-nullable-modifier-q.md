---
title: "类型“&lt;typeName&gt;”必须是值类型或约束为“Structure”的类型参数，才能与“Nullable”或可为 null 的修饰符“?”一起使用。 | Microsoft Docs"
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
  - "vbc33101"
  - "bc33101"
helpviewer_keywords: 
  - "BC33101"
ms.assetid: b3e0e4e4-87b8-4a38-a450-15233497acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型“&lt;typeName&gt;”必须是值类型或约束为“Structure”的类型参数，才能与“Nullable”或可为 null 的修饰符“?”一起使用。
只有值类型（包括结构）才可声明为可为 null。  
  
```vb#  
' Valid. Dim n? As Integer Dim m As Integer? ' Not valid. ' Dim p? As Object ' Dim q As Nullable(Of Object)  
```  
  
 **错误 ID：**BC33101  
  
### 更正此错误  
  
-   删除“?”或 `Nullable`。  
  
-   使用值数据类型。  
  
## 请参阅  
 [可以为 Null 的值类型](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)