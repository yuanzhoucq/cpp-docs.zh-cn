---
title: 容器：实现容器
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ab91316c9ee07296fbc46f9f17b3c46c71ee96f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271419"
---
# <a name="containers-implementing-a-container"></a>容器：实现容器

本文总结了实现容器的过程，向您指出了提供有关实现容器的更多详细介绍的其他文章。 它还列出了您可能需要实现的一些可选 OLE 功能以及描述这些功能的文章。

#### <a name="to-prepare-your-cwinapp-derived-class"></a>准备 CWinApp 派生类

1. 通过调用初始化 OLE 库`AfxOleInit`在`InitInstance`成员函数。

1. 调用 `CDocTemplate::SetContainerInfo` 中的 `InitInstance` 分配在就地激活嵌入项时使用的菜单和快捷键资源。 本主题的详细信息，请参阅[激活](../mfc/activation-cpp.md)。

当您使用 MFC 应用程序向导创建容器应用程序时，将为您自动提供这些功能。 请参阅[创建 MFC EXE 程序](../mfc/reference/mfc-application-wizard.md)。

#### <a name="to-prepare-your-view-class"></a>准备视图类

1. 如果您支持多个选择成为选定项，则通过维护指针或指针列表来跟踪选定项。 您的 `OnDraw` 函数必须绘制所有 OLE 项。

1. 重写 `IsSelected` 来检查当前是否选择了传递到它的项。

1. 实现`OnInsertObject`消息处理程序以显示**插入对象**对话框。

1. 实现 `OnSetFocus` 消息处理程序以将焦点从视图转移到就地活动 OLE 嵌入项。

1. 实现 `OnSize` 消息处理程序以通知 OLE 嵌入项，它需要更改其矩形才能反映其包含视图的大小更改。

由于这些功能的实现在各应用程序之间差异巨大，因此应用程序向导仅提供基本实现。 您可能必须自定义这些函数才能让应用程序正常工作。 此示例，请参阅[容器](../visual-cpp-samples.md)示例。

#### <a name="to-handle-embedded-and-linked-items"></a>处理嵌入项和链接项

1. 从派生类[COleClientItem](../mfc/reference/coleclientitem-class.md)。 此类的对象表示已嵌入或已链接到 OLE 文档的项。

1. 重写`OnChange`， `OnChangeItemPosition`，和`OnGetItemPosition`。 这些函数处理嵌入项和链接项的大小调整、定位和修改。

应用程序向导将为您，派生类，但您可能需要重写`OnChange`和在前面的过程中的步骤 2 中与其列出的其他函数。 需要为大部分应用程序自定义主干实现，因为这些函数在各应用程序之间的实现是不同的。 此示例，请参阅 MFC 示例[DRAWCLI](../visual-cpp-samples.md)并[容器](../visual-cpp-samples.md)。

您必须将大量项添加到容器应用程序的菜单结构才能支持 OLE。 有关详细信息，请参阅[菜单和资源：添加容器](../mfc/menus-and-resources-container-additions.md)。

您可能还想在容器应用程序中支持下列某些功能：

- 在编辑嵌入项时就地激活。

   有关详细信息，请参阅[激活](../mfc/activation-cpp.md)。

- 通过从服务器应用程序拖放选择来创建 OLE 项。

   有关详细信息，请参阅[拖放 (OLE)](../mfc/drag-and-drop-ole.md)。

- 链接到嵌入对象或组合容器/服务器应用程序。

   有关详细信息，请参阅[容器：高级功能](../mfc/containers-advanced-features.md)。

## <a name="see-also"></a>请参阅

[容器](../mfc/containers.md)<br/>
[容器：客户端项](../mfc/containers-client-items.md)
