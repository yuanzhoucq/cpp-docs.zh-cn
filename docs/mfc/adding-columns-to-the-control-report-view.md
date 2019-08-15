---
title: 向控件添加列（报表视图）
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 9321a582f223269ee998dccd01721f47d90eb7fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509343"
---
# <a name="adding-columns-to-the-control-report-view"></a>向控件添加列（报表视图）

> [!NOTE]
>  以下过程适用于[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md)对象。

当列表控件位于报表视图中时，将显示列，提供组织每个列表控件项的各个子项的方式。 此组织是通过列表控件的列与列表控件项的关联子项之间的一一对应来实现的。 有关子项的详细信息, 请参阅向[控件添加项](../mfc/adding-items-to-the-control.md)。 Windows 95 和 Windows 98 资源管理器的“细节”视图中提供了报表视图中列表控件的示例。 第一列将列出文件夹、文件图标和标签。 其他列将列出文件大小、文件类型、上次修改日期等。

即使列可以随时添加到列表控件，列也是仅当控件启用 `LVS_REPORT` 样式位时才可见。

每个列都有一个关联的标头项 (请参阅[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 对象, 该对象将标记列并允许用户调整列的大小。

如果列表控件支持报表视图，则需要为列表控件项的每个可能的子项添加一列。 通过准备[LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw)结构并调用[InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn)来添加列。 在添加必需的列（有时称为“标头项”）之后，您可使用属于标头控件的成员函数和样式对其进行重新排序。 有关详细信息, 请参阅对[标题控件中的项进行排序](../mfc/ordering-items-in-the-header-control.md)。

> [!NOTE]
>  如果创建的列表控件具有**LVS_NOCOLUMNHEADER**样式, 则将忽略插入列的任何尝试。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
