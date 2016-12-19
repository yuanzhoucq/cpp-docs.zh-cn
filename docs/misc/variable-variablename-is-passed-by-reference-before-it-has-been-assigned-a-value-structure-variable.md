---
title: "变量“&lt;variablename&gt;”在赋值前按引用传递（结构变量） | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42108"
  - "vbc42108"
helpviewer_keywords: 
  - "BC42108"
ms.assetid: 8f858dd7-db04-408e-ae67-e4ff2f0e5e30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 变量“&lt;variablename&gt;”在赋值前按引用传递（结构变量）
变量“\<variablename\>”在赋值前按引用传递。 可能在运行时导致 null 引用异常。 请确保在使用前对结构或所有引用成员进行了初始化  
  
 在为结构变量赋值前，过程调用将变量作为实参传递给 `ByRef` 形参。  
  
 如果从未为结构变量赋值，则每个结构成员保持其数据类型的默认值。 对于引用数据类型，默认值是 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)。 在某些情况下，读取具有 `Nothing` 值的引用成员可能导致 <xref:System.NullReferenceException>。  
  
 将参数传递给过程 `ByRef`，将使该过程能够修改以该参数的基础变量。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参阅[在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC42108  
  
### 更正此错误  
  
-   如果想让过程通过 `ByRef` 参数为结构成员赋值而成员是否已持有值并不重要，则无需进行任何操作。  
  
-   如果过程中的逻辑在赋值之前读取结构成员，且该成员是值类型，请确保过程逻辑不取决于成员是否持有其默认值。  
  
-   如果过程中的逻辑在赋值之前读取结构成员，且该成员是值类型，请确保过程逻辑能处理 `Nothing` 值。 例如，可以使用 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) 捕获 <xref:System.NullReferenceException>。  
  
## 请参阅  
 [Dim 语句](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [值类型和引用类型](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [通过值和通过引用传递参数](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)   
 [变量声明](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)   
 [结构](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Structure 语句](../Topic/Structure%20Statement.md)   
 [变量疑难解答](../Topic/Troubleshooting%20Variables%20in%20Visual%20Basic.md)