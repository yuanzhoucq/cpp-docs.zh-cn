---
title: "关于异常的疑难解答：System.Collections.Generic.KeyNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "KeyNotFoundException 类"
ms.assetid: de33f5bb-5709-46fe-b889-7105dbd24299
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Collections.Generic.KeyNotFoundException
当尝试使用不存在的键从集合中检索键或键值对时，会引发 <xref:System.Collections.Generic.KeyNotFoundException>。  
  
## 相关提示  
 **检查您正在使用的键是否存在于您尝试访问的集合中。**  
 当某个操作尝试使用集合中不存在的键来检索该集合中的元素时，会发生此异常。  
  
### 备注  
 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法可用来确定键是否存在。  
  
## 请参阅  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.KeyNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)