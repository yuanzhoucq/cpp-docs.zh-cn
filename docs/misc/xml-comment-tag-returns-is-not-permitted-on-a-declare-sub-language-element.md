---
title: "&quot;declare sub&quot; 语言元素中不允许出现 XML 注释标记 &quot;returns&quot; | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;declare sub&quot; 语言元素中不允许出现 XML 注释标记 &quot;returns&quot;
declare sub 语言元素中不允许有 XML 注释标记 "returns"。 将忽略 XML 注释。  
  
 `Declare Sub` 声明的 XML 注释不能包含 `<`returns`>` 标记。  
  
 **错误 ID：**BC42315  
  
### 更正此错误  
  
-   删除不受支持的 `<`returns`>` 标记。  
  
## 请参阅  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML 注释标记](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)   
 [使用 XML 将代码文档化](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)   
 [Declare 语句](../Topic/Declare%20Statement.md)