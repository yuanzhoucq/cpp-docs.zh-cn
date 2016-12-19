---
title: "关于异常的疑难解答：System.IdentityModel.Selectors.ServiceNotStartedException | Microsoft Docs"
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
  - "System.IdentityModel.Selectors.ServiceNotStartedException 异常"
  - "ServiceNotStartedException 异常"
ms.assetid: 6d34bab2-994a-4b0c-893d-19b5d7acf92d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IdentityModel.Selectors.ServiceNotStartedException
当用户的计算机上尚未启动 CardSpace 时，将引发 <xref:System.IdentityModel.Selectors.ServiceNotStartedException> 异常。 如果 CardSpace 尝试启动但出于某种原因而无法启动，则将引发此异常。  
  
 检查计算机上是否已安装并启用 CardSpace 服务。 通过使用 Microsoft 管理控制台 \(MMC\)，尝试手动启动 CardSpace 服务。  
  
 CardSpace 版本 1 不支持 FAT 文件系统。 在 FAT 系统上，将不会启动 CardSpace，并且将发生此异常。  
  
## 请参阅  
 <xref:System.IdentityModel.Selectors.ServiceNotStartedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)