---
title: "MAPI |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de955ecc25137f5305806ca5ba03ed15930574dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mapi"></a>MAPI
本文介绍面向客户端消息应用程序开发人员的 Microsoft 消息处理应用程序编程接口 (MAPI)。 MFC 提供了对类中的 MAPI 子集支持**CDocument**但不封装整个 API。 有关详细信息，请参阅[MFC 中的 MAPI 支持](../mfc/mapi-support-in-mfc.md)。  
  
 MAPI 是一组函数，由启用了邮件的应用程序和邮件感知应用程序用于创建、操作、传输和存储电子邮件。 它为应用程序开发人员提供了定义电子邮件的目的和内容的工具，并使他们能够灵活管理存储的电子邮件。 MAPI 还提供了公共接口，供应用程序开发人员用于独立于基础的邮件系统创建启用了邮件的应用程序和邮件感知应用程序。  
  
 消息客户端为了与 Microsoft Windows 邮件系统 (WMS) 交互提供了一个人体学接口。 此交互通常包括从与 MAPI 相容的提供程序处（如消息存储和通讯簿）请求服务。  
  
 有关 MAPI 的详细信息，请参阅指南在 Win32 消息 (MAPI) 下的 Windows sdk 的文章。  
  
## <a name="in-this-section"></a>本节内容  
 [MFC 中的 MAPI 支持](../mfc/mapi-support-in-mfc.md)  
  
## <a name="see-also"></a>请参阅  
 [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)   
 [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)   
 [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

