---
title: 虚拟列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907334"
---
# <a name="virtual-list-controls"></a>虚拟列表控件

虚拟列表控件是具有 LVS_OWNERDATA 样式的列表视图控件。 此样式使控件能够支持最多**DWORD**值的项计数（默认项计数仅扩展为**int**）。 但是，此样式提供的最大优势在于，在任何时候都只能在内存中创建一个数据项子集。 这允许虚拟列表视图控件将其自身用于大数据库信息，在这些数据库中，访问数据的特定方法已就位。

> [!NOTE]
>  除了在中`CListCtrl`提供虚拟列表功能外，MFC 还在[CListView](../mfc/reference/clistview-class.md)类中提供了相同的功能。

开发虚拟列表控件时，应注意一些兼容性问题。 有关详细信息，请参阅 Windows SDK 中 "列表视图控件" 主题的 "兼容性问题" 部分。

## <a name="handling-the-lvn_getdispinfo-notification"></a>处理 LVN_GETDISPINFO 通知

虚拟列表控件维护非常少的项信息。 除项选择和焦点信息外，所有项信息都由控件的所有者管理。 框架通过 LVN_GETDISPINFO 通知消息来请求信息。 若要提供所需的信息，虚拟列表控件（或控件本身）的所有者必须处理此通知。 可以使用[类向导](reference/mfc-class-wizard.md)轻松完成此操作（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。 生成的代码应类似于以下示例（其中`CMyDialog`拥有虚拟列表控件对象，对话框正在处理通知）：

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

在 LVN_GETDISPINFO 通知消息的处理程序中，必须检查正在请求的信息类型。 可能的值为：

- `LVIF_TEXT`必须填写*pszText*成员。

- `LVIF_IMAGE`必须填写*iImage*成员。

- `LVIF_INDENT`必须填写*iIndent*成员。

- `LVIF_PARAM`必须填写*lParam*成员。 （对于子项目，不存在。）

- `LVIF_STATE`必须填写*状态*成员。

然后，应提供向框架请求的任何信息。

下面的示例（从列表控件对象的通知处理程序的正文中获取）通过提供项的文本缓冲区和图像的信息演示了一种可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>缓存和虚拟列表控件

由于此类型的列表控件用于大型数据集，因此建议缓存请求的项数据以提高检索性能。 该框架提供了一种缓存提示机制，通过发送 LVN_ODCACHEHINT 通知消息来帮助优化缓存。

下面的示例用传递到处理程序函数的范围更新缓存。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

有关准备和维护缓存的详细信息，请参阅 Windows SDK 中 "列表视图控件" 主题的 "缓存管理" 部分。

## <a name="finding-specific-items"></a>查找特定项

当需要查找特定列表控件项时，虚拟列表控件将发送 LVN_ODFINDITEM 通知消息。 当列表视图控件收到快速访问密钥或收到 LVM_FINDITEM 消息时，将发送通知消息。 搜索信息以**LVFINDINFO**结构的形式发送，该结构是**NMLVFINDITEM**结构的成员。 通过重写`OnChildNotify`列表控件对象的函数并在处理程序的正文中来处理此消息，检查 LVN_ODFINDITEM 消息。 如果找到，则执行相应的操作。

应准备好搜索与列表视图控件提供的信息匹配的项。 如果成功，则应返回该项的索引; 如果未找到匹配项，则返回-1。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
