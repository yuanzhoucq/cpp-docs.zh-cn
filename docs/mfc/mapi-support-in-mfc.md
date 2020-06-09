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
ms.openlocfilehash: 7eff22b2a7b4c838f2967fb5217b9dec96903d0e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625571"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支持

MFC 为类中的 Microsoft 消息处理应用程序编程接口（MAPI）的子集提供支持 `CDocument` 。 具体而言， `CDocument` 包含确定最终用户计算机上是否存在邮件支持的成员函数，如果是，则启用 ID_FILE_SEND_MAIL 的 "发送邮件" 命令。 此命令的 MFC 处理程序函数允许用户通过电子邮件发送文档。

> [!TIP]
> 尽管 MFC 不封装整个 MAPI 函数集，但你仍然可以直接调用 MAPI 函数，就像你可以直接从 MFC 程序调用 Win32 API 函数一样。

在应用程序中提供 "发送邮件" 命令非常简单。 MFC 提供的实现将文档（即 `CDocument` 派生的对象）打包为附件，并将其作为邮件发送。 此附件等效于将文档内容保存（序列化）到邮件的文件保存命令。 此实现在用户计算机上的邮件客户端上调用，使用户有机会对邮件进行寻址，并向邮件添加主题和消息文本。 用户会看到他们熟悉的邮件应用程序的用户界面。 此功能由以下两个 `CDocument` 成员函数提供： `OnFileSendMail` 和 `OnUpdateFileSendMail` 。

MAPI 需要读取文件以发送附件。 如果在函数调用过程中应用程序将其数据文件保持打开状态 `OnFileSendMail` ，则需要使用允许多个进程访问该文件的共享模式打开该文件。

> [!NOTE]
> 的的重写版本 `OnFileSendMail` `COleDocument` 正确处理复合文档。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>使用 MFC 实现发送邮件命令

1. 使用 Visual C++ 菜单编辑器添加 ID_FILE_SEND_MAIL 其命令 ID 的菜单项。

   此命令 ID 由 AFXRES.H 中的框架提供。高. 可以将该命令添加到任何菜单中，但通常会将其添加到 "**文件**" 菜单。

1. 手动将以下内容添加到文档的消息映射：

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  此消息映射适用于从或派生的文档 `CDocument` ， `COleDocument` 它在这两种情况下都选取正确的基类，即使消息映射位于派生的文档类中也是如此。

1. 构建你的应用程序。

如果邮件支持可用，MFC 会启用菜单项， `OnUpdateFileSendMail` 并随后使用处理该命令 `OnFileSendMail` 。 如果邮件支持不可用，MFC 将自动删除您的菜单项，这样用户就不会看到它。

> [!TIP]
> 您可以使用类[向导](reference/mfc-class-wizard.md)将消息映射到函数，而不是按前面所述手动添加消息映射项。 有关详细信息，请参阅[将消息映射到函数](reference/mapping-messages-to-functions.md)。

有关相关信息，请参阅[MAPI](mapi.md)概述。

有关 `CDocument` 启用 MAPI 的成员函数的详细信息，请参阅：

- [CDocument：： OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument：： OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument：： OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>另请参阅

[MAPI](mapi.md)
