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
ms.openlocfilehash: 1b11bfe18443858de0dd7032f72fecadb1d6ebdd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626041"
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪贴板：使用 Windows 剪贴板

本主题介绍如何在 MFC 应用程序中使用标准 Windows 剪贴板 API。

大多数适用于 Windows 的应用程序支持将数据剪切或复制到 Windows 剪贴板，并粘贴剪贴板中的数据。 剪贴板数据格式因应用程序而异。 对于有限数量的类，框架仅支持有限数量的剪贴板格式。 在视图的 "编辑" 菜单上，通常会实现与剪贴板相关的命令（剪切、复制和粘贴）。 类库定义这些命令的命令 Id： **ID_EDIT_CUT**、 **ID_EDIT_COPY**和**ID_EDIT_PASTE**。 还定义了其消息行提示。

[框架中的消息和命令](messages-and-commands-in-the-framework.md)说明了如何通过将菜单命令映射到处理程序函数来处理应用程序中的菜单命令。 只要您的应用程序没有为 "编辑" 菜单上的 "剪贴板" 命令定义处理程序函数，它们就会保持禁用状态。 若要为剪切和复制命令编写处理函数，请在应用程序中实现选择。 若要为 "粘贴" 命令编写处理程序函数，请查询剪贴板，以查看它是否包含应用程序可以接受的格式的数据。 例如，若要启用复制命令，你可以编写类似于以下内容的处理程序：

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

剪切、复制和粘贴命令仅在某些上下文中有意义。 仅当选择了某些内容时，才应启用剪切和复制命令，并且仅当剪贴板中有内容时才应启用 "粘贴" 命令。 可以通过定义根据上下文启用或禁用这些命令的更新处理程序函数来提供此行为。 有关详细信息，请参阅[如何更新用户界面对象](how-to-update-user-interface-objects.md)。

Microsoft 基础类库为带有和类的文本编辑提供剪贴板支持 `CEdit` `CEditView` 。 OLE 类还简化了涉及 OLE 项的执行剪贴板操作。 有关 OLE 类的详细信息，请参阅[剪贴板：使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)。

实现其他编辑菜单命令（如 Undo （**ID_EDIT_UNDO**）和 Redo （**ID_EDIT_REDO**））也会留给你。 如果你的应用程序不支持这些命令，则可以使用 Visual C++ 资源编辑器轻松地将其从资源文件中删除。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [复制和粘贴数据](clipboard-copying-and-pasting-data.md)

- [使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>另请参阅

[剪贴板](clipboard.md)
