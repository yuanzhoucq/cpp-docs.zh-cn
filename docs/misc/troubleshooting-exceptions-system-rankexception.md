---
title: "关于异常的疑难解答：System.RankException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "RankException 类"
ms.assetid: ad7aa34a-f84b-4650-aaec-a75a8b85c50f
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.RankException
将具有错误维数的数组传入方法时，会引发 <xref:System.RankException> 异常。  
  
## 相关提示  
 **确保您的数组具有所需的维数。**  
 有关详细信息，Visual Basic 用户可参阅 [Visual Basic 中的数组维数](../Topic/Array%20Dimensions%20in%20Visual%20Basic.md)。  
  
 有关详细信息，C\# 用户可参阅[数组](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)。  
  
## 备注  
 由于数组下标从 0 开始，因此每一维度最小可用的下标总是为 0。  
  
## 请参阅  
 <xref:System.RankException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [数组](../Topic/Arrays%20in%20Visual%20Basic.md)