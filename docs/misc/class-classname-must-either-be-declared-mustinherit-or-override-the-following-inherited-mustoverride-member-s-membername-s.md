---
title: "类“&lt;classname&gt;”必须声明为“MustInherit”，或者重写以下“MustOverride”继承成员：&lt;membername(s)&gt; | Microsoft Docs"
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
  - "bc30610"
  - "vbc30610"
helpviewer_keywords: 
  - "BC30610"
ms.assetid: 7fba7a3b-c918-44ba-ae85-20312615c1ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类“&lt;classname&gt;”必须声明为“MustInherit”，或者重写以下“MustOverride”继承成员：&lt;membername(s)&gt;
派生自包含 `MustOverride` 成员的基类的类必须重写此类成员或使用 `MustInherit` 修饰符。  
  
 **错误 ID：**BC30610  
  
### 更正此错误  
  
-   将 `MustInherit` 修饰符添加到类定义中。  
  
-   用 `Overrides` 关键字声明重写。  
  
## 请参阅  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [不在生成中：Visual Basic 中的继承](http://msdn.microsoft.com/zh-cn/e5e6e240-ed31-4657-820c-079b7c79313c)