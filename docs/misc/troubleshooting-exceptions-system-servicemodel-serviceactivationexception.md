---
title: "关于异常的疑难解答：System.ServiceModel.ServiceActivationException | Microsoft Docs"
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
  - "ServiceActivationException 异常"
  - "System.ServiceModel.ServiceActivationException 异常"
ms.assetid: 32a3ea87-d6da-40bf-ba04-e862ac122391
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ServiceModel.ServiceActivationException
当服务未能激活时，将引发 <xref:System.ServiceModel.ServiceActivationException> 异常。  
  
## 备注  
 此异常派生自表示一类可恢复错误的 <xref:System.ServiceModel.CommunicationException>，这些错误可能会在终结点相互通信期间引发，并且应由 [!INCLUDE[vsindigo](../misc/includes/vsindigo_md.md)] 可靠客户端和服务应用程序对其进行处理。 若要阻止更为通用的 <xref:System.ServiceModel.CommunicationException> 处理程序捕捉更为具体的 <xref:System.ServiceModel.ActionNotSupportedException>，请在处理 <xref:System.ServiceModel.CommunicationException> 之前捕捉此异常。  
  
## 请参阅  
 <xref:System.ServiceModel.ServiceActivationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)