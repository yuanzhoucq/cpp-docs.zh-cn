---
title: "关于异常的疑难解答：System.NotCancelableException | Microsoft Docs"
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
  - "NotCancelableException 类"
ms.assetid: 36b82d4b-f075-4af5-993a-3e763a7e254a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.NotCancelableException
当尝试取消不可取消的操作时，将引发 `NotCancelableException`。  
  
## 相关提示  
 请不要尝试取消该操作。  
 进行这类尝试时，某些操作无法被取消并会引发此异常。 在此类情况下，应避免向用户提供取消操作的选项。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)