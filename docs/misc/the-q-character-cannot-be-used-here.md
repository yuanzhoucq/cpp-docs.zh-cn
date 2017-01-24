---
title: "此处不能使用“?”字符 | Microsoft Docs"
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
  - "bc36637"
  - "vbc36637"
helpviewer_keywords: 
  - "BC36637"
ms.assetid: a54c46e7-8fd8-4941-9fce-72f2b41b5e24
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此处不能使用“?”字符
可使用“?”字符指定值类型或结构可为 null。 它在其他情况下的用途有限。 例如，下面的代码将导致此异常。  
  
```  
' Not valid. ' #Const found = True?  
```  
  
 **错误 ID：**BC36637  
  
### 更正此错误  
  
-   从声明中删除“?”字符。  
  
## 请参阅  
 [可以为 Null 的值类型](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)