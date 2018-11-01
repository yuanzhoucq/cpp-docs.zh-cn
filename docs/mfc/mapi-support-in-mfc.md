---
title: MFC 中的 MAPI 支持
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 564ce185758d25682a88f18a23b0b11afc84a4d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567137"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支持

MFC 提供了对子集的 Microsoft 消息传送应用程序接口 (MAPI) 在类中支持`CDocument`。 具体而言，`CDocument`具有成员函数，确定是否存在于最终用户的计算机上的邮件支持，并且，如果是这样，启用其标准命令 ID 是 ID_FILE_SEND_MAIL 发送邮件命令。 此命令的 MFC 处理程序函数允许用户通过电子邮件发送文档。

> [!TIP]
>  尽管 MFC 不封装整个 MAPI 函数集，但您仍然可以调用 MAPI 函数直接，只是因为您可以直接从 MFC 程序调用 Win32 API 函数。

提供发送邮件应用程序中的命令是非常简单。 MFC 提供了要打包一个文档的实现 (也就是说， `CDocument`-派生的对象) 作为附件并将其发送作为电子邮件。 此附件相当于将保存的文件将保存命令 （序列化） 到封邮件的文档的内容。 此实现会在邮件客户端用户的计算机上，以便用户有机会解决邮件并将使用者和消息文本添加到邮件消息时调用。 用户看到熟悉的邮件应用程序的用户界面。 此功能提供的两个`CDocument`成员函数：`OnFileSendMail`和`OnUpdateFileSendMail`。

MAPI 需要读取要发送附件的文件。 如果应用程序将其数据文件保留在打开`OnFileSendMail`函数调用中，需要使用允许多个进程访问该文件的共享模式下打开该文件。

> [!NOTE]
>  重写的版本`OnFileSendMail`类`COleDocument`句柄正确复合文档。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>若要实现与 MFC 的发送邮件命令

1. 使用 Visual c + + 菜单编辑器中添加其命令 ID 是 ID_FILE_SEND_MAIL 菜单项。

   此命令 ID 提供的 AFXRES 中的框架。H. 该命令可添加到任何菜单上，但通常将其添加到**文件**菜单。

1. 手动添加到文档的消息映射的以下代码：

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  此消息映射适用于一个派生出的文档`CDocument`或`COleDocument`— 即使在消息映射中您的派生的文档类提取在任一情况下，正确的基类。

1. 构建应用程序。

如果邮件支持不可用，MFC 可以使你使用的菜单项`OnUpdateFileSendMail`，并随后处理该命令使用`OnFileSendMail`。 如果邮件支持不可用，则 MFC 都将自动删除菜单项，因此不会看到。

> [!TIP]
>  而不是手动添加的消息映射条目，如前面所述，可以使用类属性窗口将消息映射到函数。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

有关相关信息，请参阅[MAPI](../mfc/mapi.md)概述。

有关详细信息`CDocument`启用 MAPI，成员函数，请参阅：

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>请参阅

[MAPI](../mfc/mapi.md)

