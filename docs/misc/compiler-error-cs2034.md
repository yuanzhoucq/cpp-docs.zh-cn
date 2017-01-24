---
title: "编译器错误 CS2034 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2034"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2034"
ms.assetid: 72f2b785-ee23-4a1b-b12d-42d19c324d5e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS2034
声明外部别名的 \/reference 选项只能有一个文件名。 若要指定多个别名或文件名，请使用多个 \/reference 选项。  
  
 若要指定两个别名和\/或文件名，使用两个 **\/reference** 选项，如下所示：  
  
## 示例  
 下面的代码将生成错误 CS2034。  
  
```  
// CS2034.cs // compile with: /r:A1=cs2034a1.dll;A2=cs2034a2.dll // to fix, compile with: /r:A1=cs2034a1.dll /r:A2=cs2034a2.dll // CS2034 extern alias A1; extern alias A2; using System;  
```