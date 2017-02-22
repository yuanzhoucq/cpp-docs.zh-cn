---
title: "MFC 中的 MAPI 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocument 类, 和 MAPI"
  - "MFC 中的 MAPI 支持"
  - "MAPI, MFC"
  - "MFC, MAPI 支持"
  - "OnFileSendMail 方法"
  - "OnUpdateFileSendMail 方法"
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 中的 MAPI 支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC Microsoft 消息应用程序结口 \(MAPI\) 子集的支持。类提供 **CDocument**。  具体来说，**CDocument** 具有确定的成员函数邮件支持是否呈现在最终用户的计算机上，并且，如果是这样，启用标准命令 ID 是 **ID\_FILE\_SEND\_MAIL**的邮件发送命令。  此命令的 MFC 函数处理程序允许用户通过电子邮件发送文档。  
  
> [!TIP]
>  虽然 MFC 不封装整个 MAPI 函数集，则仍可以直接调用 MAPI 函数，如同可以调用 Win32 API 函数直接从 MFC 程序。  
  
 提供在应用程序中非常简单。命令发送邮件  提供 MFC 包装实现文档 \(即 **CDocument**派生的对象\) 作为和作为邮件附件发送它。  附件此与保存的文件保存命令是等效的 \(序列化\) 文档内容到邮件。  此实现需要用户计算机的邮件客户为用户提供机会处理邮件并添加用户和文本到邮件。  用户看到它们的熟悉邮件应用程序的用户界面。  两个 **CDocument** 成员函数提供此功能：`OnFileSendMail` 和 `OnUpdateFileSendMail`。  
  
 MAPI 需要读取发送文件附件。  如果应用程序数据文件将保持其打开在 `OnFileSendMail` 函数调用中，打开文件需要具有允许多个进程访问文件共享模式。  
  
> [!NOTE]
>  `OnFileSendMail` 的重写版本类的 `COleDocument` 正确处理复合文档。  
  
#### 若要实现命令发送邮件中使用 MFC  
  
1.  使用 Visual C\+\+ 编辑器添加菜单命令 ID 为 **ID\_FILE\_SEND\_MAIL**的菜单项。  
  
     此命令 ID 由在 AFXRES.H. 的框架提供。  命令可添加到全部菜单，但是，通常会添加到 **文件** 菜单。  
  
2.  手动将以下添加到文档的消息映射：  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/CPP/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  此消息映射为 **CDocument** 或 **COleDocument** 的文档中都起作用 \(在任何情况下其选取正确的基类，即使信息映射文档，在派生的类。  
  
3.  生成应用程序。  
  
 如果邮件支持可用，MFC 将具有 `OnUpdateFileSendMail` 的菜单项与后面处理 `OnFileSendMail`的命令关联。  如果无法联系邮件支持，MFC 自动移除菜单项，因此用户不会看到它。  
  
> [!TIP]
>  而不是前面所述手动添加消息映射项，可以使用类的属性窗口消息到映射函数。  有关更多信息，请参见[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
 有关相关信息，请参见 [MAPI](../mfc/mapi.md) 概述。  
  
 有关启用 MAPI 的 **CDocument** 成员函数的更多信息，请参见：  
  
-   [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)  
  
-   [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)  
  
-   [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)  
  
## 请参阅  
 [MAPI](../mfc/mapi.md)