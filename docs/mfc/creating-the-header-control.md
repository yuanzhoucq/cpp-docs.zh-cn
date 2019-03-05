---
title: 创建标题控件
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 669b13cf566f24bfcd5a29ae41af1cdb90513f73
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326135"
---
# <a name="creating-the-header-control"></a>创建标题控件

标头控件不是直接在对话框编辑器中可用的 （尽管您可以添加一个列表控件，其中包括标头控件）。

### <a name="to-put-a-header-control-in-a-dialog-box"></a>若要将标头控件放在一个对话框

1. 手动嵌入类型的成员变量[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)对话框类中。

1. 在中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)、 创建和设置的样式`CHeaderCtrl`、 定位它，并将其显示。

1. 将项添加到标头控件。

1. 使用属性窗口对于任何标头控件通知消息您映射对话框类中的处理程序函数需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>若要将标头控件放在视图 (不 CListView)

1. 嵌入[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)在视图类中的对象。

1. 设置样式、 位置，并在视图中显示标头控件窗口[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成员函数。

1. 将项添加到标头控件。

1. 使用属性窗口的任何标头控件通知消息映射的 view 类中的处理程序函数需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

在任一情况下，创建视图或对话框对象时创建嵌入的控件对象。 然后必须调用[CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)创建控件窗口。 若要定位的控件，调用[CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout)来确定控件的初始大小和位置以及[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)设置所需的位置。 然后添加项，如中所述[将项添加到标头控件](../mfc/adding-items-to-the-header-control.md)。

有关详细信息，请参阅[创建标头控件](/windows/desktop/Controls/header-controls)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
