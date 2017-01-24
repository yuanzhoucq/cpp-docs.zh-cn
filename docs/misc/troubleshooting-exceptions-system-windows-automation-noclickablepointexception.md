---
title: "关于异常的疑难解答：System.Windows.Automation.NoClickablePointException | Microsoft Docs"
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
  - "EHWANoClickablePoint"
helpviewer_keywords: 
  - "NoClickablePointException 异常"
  - "System.Windows.Automation.NoClickablePointException 异常"
ms.assetid: faf8c262-8e17-425c-ab65-7b38cd1828af
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Windows.Automation.NoClickablePointException
当对没有可单击的点的 UI <xref:System.Windows.Automation.NoClickablePointException> 调用 <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> 时，将引发某种异常，而 <xref:System.Windows.Automation.AutomationElement> 异常将包含有关这种异常的信息。  
  
## 备注  
 如果最小化应用程序窗口或者元素位于屏幕之外，则可能会引发此异常。  
  
## 请参阅  
 <xref:System.Windows.Automation.NoClickablePointException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)