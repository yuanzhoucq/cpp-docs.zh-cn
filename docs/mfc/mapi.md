---
title: "MAPI | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "电子邮件, 启用"
  - "启用针对邮件的应用程序"
  - "启用针对 MAPI 的应用程序"
  - "邮件, 启用您的应用程序"
  - "MFC 中的 MAPI 支持"
  - "MAPI, MFC"
  - "消息传递, 客户端应用程序"
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MAPI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍消息客户端应用程序开发人员执行 Microsoft 消息处理应用程序编程接口 \(MAPI\) 。  在类 **CDocument**中MFC 提供支持 MAPI的一部分，但不封装整个 API。  有关详细信息，请参阅 [MAPI Support in MFC](../mfc/mapi-support-in-mfc.md)。  
  
 MAPI 为邮件实现和邮件识别应用程序使用的创建、操作、传输和存储邮件消息的的一组函数。  为应用开发人员工具定义邮件消息的目的和内容并在它们所存储邮件消息的管理中提供灵活性。  MAPI 还提供公共接口，该接口时应用程序开发人员可以创建邮件实现和邮件识别应用程序，这是独立的基础消息系统。  
  
 客户端传报程序用作交互提供可相互关系的 Microsoft Windows 消息系统 \(WMS\)。  此交互通常包括 从匹配的CLS请求服务器，例如消息和存储通讯簿。  
  
 有关 MAPI 的更多信息，请参见在 Win32 消息 \(MAPI\) 的指导下的本文 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]  
  
## 本节内容  
 [MFC 中支持MAPI](../mfc/mapi-support-in-mfc.md)  
  
## 请参阅  
 [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)   
 [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)   
 [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)