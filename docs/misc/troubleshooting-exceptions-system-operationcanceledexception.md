---
title: "关于异常的疑难解答：System.OperationCanceledException | Microsoft Docs"
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
  - "OperationCanceledException 类"
ms.assetid: 275e2887-7491-432b-9b80-a21bb794be29
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.OperationCanceledException
如果在 <xref:System.OperationCanceledException> 设置为 <xref:Microsoft.VisualBasic.FileIO.UICancelOption> 的情况下执行某一操作，然后取消了该操作，则将引发 `ThrowException`。  
  
## 相关提示  
 如果您不希望引发此异常，请将 <xref:System.OperationCanceledException> 设置为 `DoNothing`。  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption> 的默认值为 `ThrowException`。 如果您不希望当用户取消操作时引发此异常，请将枚举值设置为 `DoNothing`。  
  
## 请参阅  
 <xref:System.OperationCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)