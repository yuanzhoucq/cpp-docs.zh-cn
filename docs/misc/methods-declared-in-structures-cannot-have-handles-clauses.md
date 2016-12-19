---
title: "结构中声明的方法不能包含“Handles”子句 | Microsoft Docs"
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
  - "vbc30728"
  - "bc30728"
helpviewer_keywords: 
  - "BC30728"
ms.assetid: 64c70bb5-3696-4865-8194-328394c2b4b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 结构中声明的方法不能包含“Handles”子句
结构方法不能使用 `Handles` 关键字来处理事件。  
  
 **错误 ID：**BC30728  
  
### 更正此错误  
  
-   请考虑重新设计作为类的结构。  
  
     可以使用 `AddHandler` 将事件与事件处理程序关联在结构中，前提是该结构实现的是接口中定义的事件处理程序。  
  
## 请参阅  
 [结构和类](../Topic/Structures%20and%20Classes%20\(Visual%20Basic\).md)   
 [不在生成中：类：对象的蓝图](http://msdn.microsoft.com/zh-cn/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)   
 [不在生成中：AddHandler 和 RemoveHandler](http://msdn.microsoft.com/zh-cn/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)