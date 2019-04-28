---
title: 剪贴板：使用 Windows 剪贴板
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 49111e4efd2a12264d61030fe038d80b974514c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326984"
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪贴板：使用 Windows 剪贴板

本主题介绍如何使用 MFC 应用程序中的标准 Windows 剪贴板 API。

适用于 Windows 的大多数应用程序支持剪切或复制到 Windows 剪贴板数据和从剪贴板粘贴数据。 剪贴板数据格式应用程序而异。 该框架支持的有限数量的类仅有限的数量的剪贴板格式。 通常情况下，您将实现剪贴板相关的命令，剪切、 复制和粘贴-为您的视图编辑菜单上。 类库定义了这些命令的命令 Id:**ID_EDIT_CUT**， **ID_EDIT_COPY**，和**ID_EDIT_PASTE**。 此外定义了其消息行提示。

[消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)说明如何通过将菜单命令映射到处理程序函数处理你的应用程序中的菜单命令。 只要你的应用程序没有在编辑菜单上定义的剪贴板命令的处理程序函数，它们将保持禁用状态。 若要编写的剪切和复制命令的处理程序函数，在应用程序中实现所选内容。 若要编写粘贴命令处理程序函数，请查询剪贴板上以查看它是否包含你的应用程序可以接受的格式中的数据。 例如，若要启用复制命令，您可以编写一个处理程序类似于以下内容：

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

剪切、 复制和粘贴命令仅在某些上下文中有意义。 仅当选择了内容，且粘贴命令仅当内容是在剪贴板中时，应启用剪切和复制命令。 可以通过定义启用或禁用这些命令具体取决于上下文的更新处理程序函数来提供此行为。 有关详细信息，请参阅[如何更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)。

Microsoft 基础类库提供剪贴板支持进行文本编辑与`CEdit`和`CEditView`类。 OLE 类还简化了实现涉及 OLE 项的剪贴板操作。 OLE 类的详细信息，请参阅[剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。

实现其他编辑菜单命令，例如撤消 (**ID_EDIT_UNDO**) 和重做 (**ID_EDIT_REDO**)，同时也预留给你。 如果你的应用程序不支持这些命令，你可以轻松地删除它们使用视觉对象的资源文件从C++资源编辑器。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)

- [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>请参阅

[剪贴板](../mfc/clipboard.md)
