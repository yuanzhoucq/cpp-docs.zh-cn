---
title: 虚拟列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375520"
---
# <a name="virtual-list-controls"></a>虚拟列表控件

虚拟列表控件是具有LVS_OWNERDATA样式的列表视图控件。 此样式使控件能够支持最多到**DWORD**的项计数（默认项计数仅扩展到**int**）。 但是，此样式提供的最大优势是能够在任何时候仅具有内存中的数据项子集。 这允许虚拟列表视图控件适合用于大型信息数据库，其中已具有访问数据的特定方法。

> [!NOTE]
> 除了在 中`CListCtrl`提供虚拟列表功能外，MFC 还在[CListView](../mfc/reference/clistview-class.md)类中提供了相同的功能。

在开发虚拟列表控件时，您应该注意一些兼容性问题。 有关详细信息，请参阅 Windows SDK 中的"列表-查看控件"主题的兼容性问题部分。

## <a name="handling-the-lvn_getdispinfo-notification"></a>处理LVN_GETDISPINFO通知

虚拟列表控件维护的项目信息很少。 除物料选择和焦点信息外，所有物料信息都由控件的所有者管理。 框架通过LVN_GETDISPINFO通知消息请求信息。 要提供请求的信息，虚拟列表控件的所有者（或控件本身）必须处理此通知。 这可以很容易地使用[类向导](reference/mfc-class-wizard.md)完成（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。 由此产生的代码应类似于以下示例（其中`CMyDialog`拥有虚拟列表控件对象，对话框正在处理通知）：

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

在LVN_GETDISPINFO通知消息的处理程序中，必须检查请求的信息类型。 可能的值包括：

- `LVIF_TEXT`必须填写*pszText*成员。

- `LVIF_IMAGE`必须填写*iImage*成员。

- `LVIF_INDENT`必须填写*iIndent*成员。

- `LVIF_PARAM`必须填写*lParam*成员。 （子项不存在。

- `LVIF_STATE`必须填写*国务委员*。

然后，您应该提供请求回框架的任何信息。

以下示例（从列表控件对象的通知处理程序正文中）演示了一种可能的方法，方法是为项目的文本缓冲区和图像提供信息：

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>缓存和虚拟列表控件

由于这种类型的列表控件适用于大型数据集，因此建议您缓存请求的项数据以提高检索性能。 该框架提供了一种缓存提示机制，通过发送LVN_ODCACHEHINT通知消息来帮助优化缓存。

下面的示例使用传递给处理程序函数的范围更新缓存。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

有关准备和维护缓存的详细信息，请参阅 Windows SDK 中的"列表查看控件"主题的缓存管理部分。

## <a name="finding-specific-items"></a>查找特定项目

当需要找到特定列表控件项时，虚拟列表控件将发送LVN_ODFINDITEM通知消息。 当列表视图控件收到快速密钥访问或收到LVM_FINDITEM消息时，将发送通知消息。 搜索信息以**LVFINDINFO**结构的形式发送，该结构是**NMLVFINDITEM**结构的成员。 通过重写列表控件对象的`OnChildNotify`功能以及处理程序正文内来处理此消息，请检查LVN_ODFINDITEM消息。 如果找到，则执行相应的操作。

您应该准备搜索与列表视图控件提供的信息匹配的项。 如果成功，则应返回项的索引;如果未找到匹配项，则应返回 -1。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
