---
title: "命名空间名称“&lt;namespacename1&gt;”的大小写与文件“&lt;filepath&gt;”中命名空间名称 “&lt;namespacename2&gt;”的大小写不匹配 | Microsoft Docs"
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
  - "vbc40055"
  - "bc40055"
helpviewer_keywords: 
  - "BC40055"
ms.assetid: adaac2fe-1513-4234-afe7-633a76089f36
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 命名空间名称“&lt;namespacename1&gt;”的大小写与文件“&lt;filepath&gt;”中命名空间名称 “&lt;namespacename2&gt;”的大小写不匹配
命名空间在项目中出现多次，但具有不同的大小写。  
  
 *大小写*是指在编程元素的名称中使用大写字符和小写字符。 Visual Basic 不区分大小写，但公共语言运行时 \(CLR\) 区分大小写。 相关详细信息，请参阅[已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)中的"名称的大小写区分"。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC40055  
  
### 更正此错误  
  
-   作为预防措施，应始终在对命名空间的各个引用中使用相同的大小写。 这可以防止公共语言运行时进行错误解释。  
  
## 请参阅  
 [Namespace 语句](../Topic/Namespace%20Statement.md)   
 [Visual Basic 中的命名空间](../Topic/Namespaces%20in%20Visual%20Basic.md)   
 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic 命名约定](../Topic/Visual%20Basic%20Naming%20Conventions.md)