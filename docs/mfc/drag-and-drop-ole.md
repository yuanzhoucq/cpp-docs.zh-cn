---
title: OLE 拖放
description: Microsoft 基础类（MFC） OLE 拖放、如何实现放置源以及如何自定义拖放的概述。
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: c601e8f0324510346513dc8da48dd1a83c95bceb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855432"
---
# <a name="ole-drag-and-drop"></a>OLE 拖放

OLE 的拖放功能主要是复制并粘贴数据的快捷方式。 当您使用剪贴板复制或粘贴数据时，需要执行一些步骤。 选择数据，然后从 "**编辑**" 菜单中选择 "**剪切**" 或 "**复制**"。 然后移动到目标应用或窗口，并将光标置于目标位置。 最后，从菜单中选择 "**编辑** > "**粘贴**"。

OLE 拖放功能不同于文件管理器拖放机制。 文件管理器只能处理文件名，专用于将文件名传递给应用程序。 OLE 中的拖放更为常见。 利用此功能，您可拖放还可放置在剪贴板上的任何数据。

如果使用 OLE 拖放，则此过程可减少两个步骤。 从 "源" 窗口中选择数据（"放置源"），然后将其拖动到目标位置（"drop target"）。 通过释放鼠标按钮将其删除。 此操作无需菜单，并且比复制/粘贴序列快。 只有一个要求：拖放源和放置目标必须是打开的，并且在屏幕上至少部分可见。

使用 OLE 拖放，可以轻松地将数据从一个位置传输到另一个位置：文档内、不同文档之间或应用程序之间。 它可以在容器或服务器应用程序中实现。 任何应用程序都可以是放置源，也可以是拖放目标。 如果应用程序同时实现了放置源和放置目标支持，则可以在子窗口之间或在一个窗口中拖放。 此功能使应用程序更易于使用。

[数据对象和数据源（OLE）](../mfc/data-objects-and-data-sources-ole.md)一文介绍了如何在应用程序中实现数据传输。 它还有助于检查 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)。

## <a name="implement-a-drop-source"></a>实现放置源

若要使应用程序向拖放操作提供数据，请实现放置源。 放置源的基本实现相对简单。 第一步是确定开始拖动操作的事件。 建议的用户界面准则定义拖动操作的开始时间，就像在某些选定数据内的某个点上出现**WM_LBUTTONDOWN**事件时。 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)遵循这些准则。

如果你的应用程序是一个容器，并且所选数据是 `COleClientItem`类型的链接或嵌入对象，请调用其 `DoDragDrop` 成员函数。 否则，构造一个 `COleDataSource` 对象，使用选择对其进行初始化，并调用该数据源对象的 `DoDragDrop` 成员函数。 如果你的应用程序是服务器，则使用 `COleServerItem::DoDragDrop`。 有关自定义标准拖放行为的信息，请参阅[自定义拖](#customize-drag-and-drop)放部分。

如果 `DoDragDrop` 返回**DROPEFFECT_MOVE**，请立即删除源文档中的源数据。 `DoDragDrop` 中的任何其他返回值都不会对放置源产生任何影响。

有关详细信息，请参阅[OLE 数据对象和数据源：创建和销毁](../mfc/data-objects-and-data-sources-creation-and-destruction.md)和[OLE 数据对象和数据源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a>实现放置目标

实现放置目标比放置源要稍微复杂一些，但仍相对简单。

### <a name="to-implement-an-ole-drop-target"></a>实现 OLE 放置目标

1. 如果它尚不存在，请在应用程序的 `InitInstance` 成员函数中添加对 `AfxOleInit` 的调用。 此调用是初始化 OLE 库所必需的。

1. 将成员变量添加到要作为放置目标的应用程序中的每个视图。 此成员变量的类型必须为 `COleDropTarget` 或从其派生的类。

1. 从处理**WM_CREATE**消息（通常 `OnCreate`）的视图类的函数中，调用新成员变量的 `Register` 成员函数。 当你的视图被销毁时，将自动为你调用 `Revoke`。

1. 重写以下函数。 如果需要在整个应用程序中具有相同的行为，请在视图类中重写这些函数。 如果要在隔离情况下修改行为，或想要在非`CView` 窗口中进行删除，请在 `COleDropTarget`派生类中重写这些函数。

   | 替代 | 允许 |
   | -------- | -------- |
   | `OnDragEnter` | 在窗口中执行删除操作。 当光标首次进入窗口时调用。 |
   | `OnDragLeave` | 拖动操作离开指定窗口时的特殊行为。 |
   | `OnDragOver` | 在窗口中执行删除操作。 当光标拖动到窗口中时调用。 |
   | `OnDrop` | 处理被删除到指定窗口中的数据。 |
   | `OnScrollBy` | 目标窗口中需要滚动时的特殊行为。 |

请参阅 MAINVIEW。作为 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)一部分的 CPP 文件，用于举例说明这些函数是如何协同工作的。

有关详细信息，请参阅[OLE 数据对象和数据源：创建和销毁](../mfc/data-objects-and-data-sources-creation-and-destruction.md)和[OLE 数据对象和数据源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a>自定义拖放

拖放功能的默认实现对大多数应用程序都够用。 但是，某些应用程序可能要求你更改此标准行为。 本部分介绍更改这些默认设置所需的步骤。 您可以使用此方法将不支持复合文档的应用程序转换为丢弃源。

如果要自定义标准 OLE 拖放行为，或者具有非 OLE 应用程序，则必须创建一个包含数据的 `COleDataSource` 对象。 当用户启动拖放操作时，你的代码从此对象（而非支持拖放操作的其他类）应调用 `DoDragDrop` 函数。

或者，您也可以创建一个 `COleDropSource` 对象来控制放置和重写其函数，具体取决于要更改的行为的类型。 此放置源对象随后会传递给 `COleDataSource::DoDragDrop` 以更改这些函数的默认行为。 这些不同的选项在您支持应用程序中的拖放操作的方式上提供了极大的灵活性。 有关数据源的详细信息，请参阅文章[数据对象和数据源（OLE）](../mfc/data-objects-and-data-sources-ole.md)。

您可以重写以下函数以自定义拖放操作：

| 替代 | 以自定义 |
| -------- | ------------ |
| `OnBeginDrag` | 调用 `DoDragDrop`后，拖动操作的开始方式。 |
| `GiveFeedback` | 其他放置结果的可视反馈，如光标外观。 |
| `QueryContinueDrag` | 拖放操作的终止。 此函数使您能够在拖动操作期间检查键修改键状态。 |

## <a name="see-also"></a>另请参阅

[OLE](../mfc/ole-in-mfc.md)\
[OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-ole.md)\
[OLE 数据对象和数据源：创建和析构](../mfc/data-objects-and-data-sources-creation-and-destruction.md)\
[OLE 数据对象和数据源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\
[COleClientItem：:D odragdrop](../mfc/reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource 类](../mfc/reference/coledatasource-class.md)\
[COleDataSource：:D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)\
[COleDropSource 类](../mfc/reference/coledropsource-class.md)\
[COleDropTarget 类](../mfc/reference/coledroptarget-class.md)\
[CView：： System.windows.uielement.ondragleave](../mfc/reference/cview-class.md#ondragleave)
