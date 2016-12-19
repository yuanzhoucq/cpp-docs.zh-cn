---
title: "关于异常的疑难解答：System.DeploymentFramework.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DependentPlatformMissingException 类, 疑难解答"
ms.assetid: fee1ca1c-0f0b-483b-b8ab-3743dfdda038
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.DeploymentFramework.DependentPlatformMissingException
当应用程序依赖于未安装在此客户端上的某个组件时，会引发 `T:System.DeploymentFramework.DependentPlatformMissingException` 异常。 可能的原因包括错误的操作系统或者部署应用程序的计算机上的 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 版本错误。  
  
## 相关提示  
 **请检查应用程序所需要的所有程序集是否都已安装在目标计算机上。**  
 每次尝试使用 Windows Installer 的安装开始时都会检查用户的计算机上是否存在该安装程序，如果不存在，则检查计算机是否已准备好安装 Windows Installer。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)