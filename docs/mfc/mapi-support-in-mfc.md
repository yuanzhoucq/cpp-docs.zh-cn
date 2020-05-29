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
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356991"
---
# <a name="mapi-support-in-mfc"></a>MFC 中的 MAPI 支持

MFC 为类`CDocument`中的 Microsoft 消息应用程序接口 （MAPI） 的子集提供支持。 具体而言`CDocument`，具有确定最终用户计算机上是否存在邮件支持的成员函数，如果是，则启用其标准命令 ID ID_FILE_SEND_MAIL的"发送邮件"命令。 此命令的 MFC 处理程序功能允许用户通过电子邮件发送文档。

> [!TIP]
> 尽管 MFC 不封装整个 MAPI 函数集，您仍然可以直接调用 MAPI 函数，就像可以直接从 MFC 程序调用 Win32 API 函数一样。

在应用程序中提供"发送邮件"命令非常简单。 MFC 提供实现，将文档（即`CDocument`派生对象）打包为附件，并将其作为邮件发送。 此附件等效于文件保存命令，该命令将文档的内容保存到邮件中（序列化）。 此实现要求用户计算机上的邮件客户端为用户提供处理邮件和向邮件添加主题和邮件文本的机会。 用户可以看到他们熟悉的邮件应用程序的用户界面。 此功能由两`CDocument`个成员函数提供：`OnFileSendMail`和`OnUpdateFileSendMail`。

MAPI 需要读取文件才能发送附件。 如果应用程序在`OnFileSendMail`函数调用期间保持其数据文件处于打开状态，则需要使用允许多个进程访问该文件的共享模式打开该文件。

> [!NOTE]
> `OnFileSendMail`类重写版本`COleDocument`可正确处理复合文档。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>使用 MFC 实现"发送邮件"命令

1. 使用 Visual C++ 菜单编辑器添加命令 ID 为ID_FILE_SEND_MAIL的菜单项。

   此命令 ID 由 AFXRES 中的框架提供。H。 该命令可以添加到任何菜单，但它通常添加到 **"文件"** 菜单中。

1. 手动将以下内容添加到文档的消息映射中：

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  此消息映射适用于从任一或`CDocument``COleDocument`— 在任一情况下拾取正确的基类的文档，即使消息映射位于派生的文档类中也是如此。

1. 生成应用程序。

如果邮件支持可用，MFC 将启用菜单项，`OnUpdateFileSendMail`然后使用 处理命令`OnFileSendMail`。 如果邮件支持不可用，MFC 会自动删除您的菜单项，以便用户不会看到它。

> [!TIP]
> 您可以使用[类向导](reference/mfc-class-wizard.md)将消息映射到函数，而不是手动添加前面描述的消息映射条目。 有关详细信息，请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

有关详细信息，请参阅[MAPI](../mfc/mapi.md)概述。

有关启用 MAPI`CDocument`的成员函数的详细信息，请参阅：

- [CDocument：：在文件发送邮件](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument：：更新文件发送邮件](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COle 文档：：在文件发送邮件](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>另请参阅

[MAPI](../mfc/mapi.md)
