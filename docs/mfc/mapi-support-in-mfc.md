---
title: MFC 中的 MAPI 支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5d6498d1ecb20b47070cb26bf1a9d732340e266
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349657"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支持
MFC 提供了对子集的 Microsoft 消息处理应用程序程序接口 (MAPI) 类中支持**CDocument**。 具体而言， **CDocument**具有确定邮件支持是否在最终用户的计算机上存在的成员函数，并且，如果是这样，启用其标准命令 id 的发送邮件命令**ID_FILE_SEND_MAIL**. 此命令的 MFC 处理程序函数允许用户通过电子邮件发送文档。  
  
> [!TIP]
>  尽管 MFC 不封装整个 MAPI 函数集，但仍然可以调用 MAPI 函数直接，只需为可直接从 MFC 程序中调用 Win32 API 函数。  
  
 提供发送邮件应用程序中的命令是非常简单。 MFC 提供的实现来打包文档 (即， **CDocument**-派生对象) 以附件形式并将其作为电子邮件发送。 此附件相当于将保存的文件保存命令 （序列化） 到邮件的文档的内容。 此实现中调用邮件客户端用户的计算机上，可以向用户授予机会，将邮件发送，并将使用者和消息文本添加到邮件消息。 用户看到其熟悉的邮件应用程序的用户界面。 此功能提供的两个**CDocument**成员函数：`OnFileSendMail`和`OnUpdateFileSendMail`。  
  
 MAPI 需要读取要发送附件的文件。 如果应用程序将其数据文件保留在打开`OnFileSendMail`函数调用，该文件必须使用允许多个进程访问该文件的共享模式下打开。  
  
> [!NOTE]
>  重写的版本`OnFileSendMail`类`COleDocument`正确句柄复合文档。  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>若要实现具有 MFC 的发送邮件命令  
  
1.  使用 Visual c + + 菜单编辑器将添加其命令 ID 是菜单项**ID_FILE_SEND_MAIL**。  
  
     此命令 ID 是由在 AFXRES framework 提供的。H。 该命令可以添加到任何菜单上，但通常将其添加到**文件**菜单。  
  
2.  手动将以下代码添加到文档的消息映射：  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  此消息映射适用于从派生文档**CDocument**或**COleDocument** — 即使消息映射是在派生的文档类拾取在任一情况下，正确的基类。  
  
3.  生成你的应用程序。  
  
 MFC 邮件支持是否可用，使你的菜单项与`OnUpdateFileSendMail`并随后处理该命令与`OnFileSendMail`。 如果邮件支持不可用，则 MFC 都将自动删除菜单项，以便用户将不会看到它。  
  
> [!TIP]
>  而不是手动添加的消息映射条目，如上文所述，你可以使用类属性窗口将消息映射到函数。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
 有关相关信息，请参阅[MAPI](../mfc/mapi.md)概述。  
  
 有关详细信息**CDocument**成员函数，MAPI，请参阅：  
  
-   [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>请参阅  
 [MAPI](../mfc/mapi.md)

