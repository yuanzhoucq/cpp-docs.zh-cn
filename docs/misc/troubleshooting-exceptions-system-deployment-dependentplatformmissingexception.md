---
title: "关于异常的疑难解答：System.Deployment.DependentPlatformMissingException | Microsoft Docs"
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
  - "DependentPlatformMissingException 类"
ms.assetid: 2343eb4f-f23f-4b6c-a65c-1f93c3e6ea36
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Deployment.DependentPlatformMissingException
尝试在不兼容的计算机上运行应用程序时，将引发 `T:System.Deployment.DependentPlatformMissingException` 异常。 当目标计算机上安装了错误的操作系统或错误版本的 .NET Framework 时，可能发生此情况。  
  
## 相关提示  
 **确保在目标计算机上安装了应用程序需要的所有程序集。**  
 每次尝试使用 Windows Installer 的安装开始时都会检查用户的计算机上是否存在该安装程序，如果不存在，则检查计算机是否已准备好安装 Windows Installer。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)