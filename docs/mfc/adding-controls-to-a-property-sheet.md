---
title: 将控件添加到属性表
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 527c0a5ef6e9dc4fcc9d7668c12e15ec956b0e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616064"
---
# <a name="adding-controls-to-a-property-sheet"></a>将控件添加到属性表

默认情况下，属性表将为属性页、选项卡索引和“确定”、“取消”和“应用”按钮分配窗口区域。 （无模式属性表没有 "确定"、"取消" 和 "应用" 按钮。）您可以向属性表中添加其他控件。 例如，您可以在属性页区域右侧添加预览窗口，以便为用户显示对外部对象应用当前设置的效果。

可以在 `OnCreate` 处理程序中向属性表对话框添加控件。 容纳附加控件通常需要扩展属性表对话框的大小。 调用**CPropertySheet：： OnCreate**基类后，调用[GetWindowRect](reference/cwnd-class.md#getwindowrect)以获取当前已分配属性表窗口的宽度和高度，展开该矩形的维度，然后调用[MoveWindow](reference/cwnd-class.md#movewindow)以更改属性表窗口的大小。

## <a name="see-also"></a>另请参阅

[属性表](property-sheets-mfc.md)<br/>
[CPropertyPage 类](reference/cpropertypage-class.md)<br/>
[CPropertySheet 类](reference/cpropertysheet-class.md)
