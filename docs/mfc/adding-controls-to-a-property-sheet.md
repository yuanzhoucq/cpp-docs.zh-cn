---
title: 将控件添加到属性表 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0783571ed77d3d8dfaca69edf06330e62d8e98d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398485"
---
# <a name="adding-controls-to-a-property-sheet"></a>将控件添加到属性表

默认情况下，属性表将为属性页、选项卡索引和“确定”、“取消”和“应用”按钮分配窗口区域。 （无模式的属性表没有“确定”、“取消”和“应用”按钮。）您可以将其他控件添加到属性表中。 例如，您可以在属性页区域右侧添加预览窗口，以便为用户显示对外部对象应用当前设置的效果。

可以在 `OnCreate` 处理程序中向属性表对话框添加控件。 容纳附加控件通常需要扩展属性表对话框的大小。 在调用基类**cpropertysheet:: Oncreate**，调用[GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect)若要获取的宽度和高度的当前分配的属性表窗口，请展开矩形的尺寸，并调用[MoveWindow](../mfc/reference/cwnd-class.md#movewindow)若要更改的属性表窗口的大小。

## <a name="see-also"></a>请参阅

[属性表](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage 类](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet 类](../mfc/reference/cpropertysheet-class.md)
