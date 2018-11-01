---
title: 虚拟列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: b9da918017d300d7af61b1fd3ab27869e136bb8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573647"
---
# <a name="virtual-list-controls"></a>虚拟列表控件

虚拟列表控件是具有 LVS_OWNERDATA 样式的列表视图控件。 此样式允许控件以最多支持项计数**DWORD** (默认项计数仅扩展到**int**)。 但是，此样式所提供的最大优点是能够在任何时候在内存中仅具有数据项的子集。 这允许虚拟列表视图控件以适合用于大型数据库的信息，其中的特定方法的访问的数据均已就位。

> [!NOTE]
>  除了提供虚拟列表中的功能之外`CListCtrl`，MFC 还提供了在相同的功能[CListView](../mfc/reference/clistview-class.md)类。

有一些兼容性问题，应注意的开发虚拟列表控件时。 有关详细信息，请参阅 Windows SDK 中的列表视图控件主题的兼容性问题部分。

## <a name="handling-the-lvngetdispinfo-notification"></a>处理 LVN_GETDISPINFO 通知

虚拟列表控件维护很少的项信息。 除了项选择和焦点的信息，由该控件的所有者管理项的所有信息。 由框架通过 LVN_GETDISPINFO 通知消息请求信息。 若要提供所需的信息，请虚拟列表控件 （或控件本身） 的所有者必须处理此通知。 可以轻松地完成这使用属性窗口 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。 生成的代码应类似于下面的示例 (其中`CMyDialog`拥有虚拟列表控件对象，该对话框处理通知):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

LVN_GETDISPINFO 通知消息的处理程序，必须检查以查看哪种类型的信息为其请求。 可能的值为：

- `LVIF_TEXT` *PszText*成员必须填写。

- `LVIF_IMAGE` *IImage*成员必须填写。

- `LVIF_INDENT` *IIndent*成员必须填写。

- `LVIF_PARAM` *LParam*成员必须填写。 （不存在子项目）

- `LVIF_STATE` *状态*成员必须填写。

然后应提供所有请求的信息返回到框架。

下面的示例 （摘自列表控件对象的通知处理程序的正文） 通过提供的文本缓冲区和项的图像的信息演示了一个可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>缓存和虚拟列表控件

由于此类型的列表控件适用于大型数据集，建议你缓存请求的项数据，以提高检索性能。 框架提供缓存提示的机制，以帮助优化缓存通过发送 LVN_ODCACHEHINT 通知消息。

下面的示例使用传递给处理程序函数的范围更新缓存。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

有关准备和维护缓存的详细信息，请参阅 Windows SDK 中的列表视图控件主题的缓存管理部分。

## <a name="finding-specific-items"></a>查找特定项

虚拟列表控件时，需要找到特定的列表控件项会发送 LVN_ODFINDITEM 通知消息。 列表视图控件接收键的快速访问时收到 LVM_FINDITEM 消息或发送通知消息。 搜索信息发送中的窗体**LVFINDINFO**结构，它是成员的**NMLVFINDITEM**结构。 通过重写处理此消息`OnChildNotify`在列表中的函数控制对象和内部处理程序的正文中，检查 LVN_ODFINDITEM 消息。 如果找到，请执行相应的措施。

你应准备好项列表视图控件提供的信息相匹配的搜索。 如果不找到任何匹配项，应返回其索引的项，如果成功，则为-1。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

