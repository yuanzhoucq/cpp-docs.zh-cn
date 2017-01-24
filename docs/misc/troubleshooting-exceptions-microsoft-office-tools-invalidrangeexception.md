---
title: "关于异常的疑难解答：Microsoft.Office.Tools.InvalidRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.Office.Tools.InvalidRangeException 异常"
ms.assetid: 0deea25b-1152-40b6-89e2-e2e9c85f7dc0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：Microsoft.Office.Tools.InvalidRangeException
以编程方式创建范围跨越多个区域的视图控件时，将引发 <xref:Microsoft.Office.Tools.InvalidRangeException> 异常。  
  
## 相关提示  
 确保范围所覆盖的区域不与其他范围重叠。  
 范围不能重叠。  
  
 确保以编程方式创建视图控件时，该视图控件只包含单个区域  
 -   确保以编程方式创建视图控件时，该视图控件只包含单个区域，即所有单元格都在一起。  
  
## 请参阅  
 <xref:Microsoft.Office.Tools.InvalidRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)