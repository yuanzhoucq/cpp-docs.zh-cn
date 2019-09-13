---
title: 调节按钮样式
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907861"
---
# <a name="spin-button-styles"></a>调节按钮样式

数值调节钮的许多设置（[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)）由样式控制。 您可以使用[类向导](reference/mfc-class-wizard.md)设置以下样式。

- **方向**垂直或水平。 控制箭头按钮的方向。 与 UDS_HORZ 样式关联的。

- **对齐**未附加、左或右的一个。 控制数字调整按钮的位置。 向左和向右定位 "合作者" 窗口旁的数值调节钮。 将减少合作者窗口的宽度以容纳数值调节钮。 与 UDS_ALIGNLEFT 和 UDS_ALIGNRIGHT 样式关联的。

- **自动合作者**自动选择 "Z 顺序" 中的上一个窗口作为 "合作者" 窗口。 在对话框模板中，这是 tab 键顺序中位于数值调节钮之前的控件。 与 UDS_AUTOBUDDY 样式关联的。

- **设置好友整数**导致数值调节钮控件在当前位置更改时递增和递减合作者窗口的标题。 与 UDS_SETBUDDYINT 样式关联的。

- **无成千上万**不会在合作者窗口标题的值中插入千位分隔符。 与 UDS_NOTHOUSANDS 样式关联的。

    > [!NOTE]
    >  如果要使用对话框数据交换（DDX）从合作者控件获取整数值，请设置此样式。 `DDX_Text`不接受嵌入的千位分隔符。

- **换行**导致位置 "换行"，因为该值在控件范围之外递增或递减。 与 UDS_WRAP 样式关联的。

- **箭头键**导致数值调节钮在按向上键和向下键时递增或递减位置。 与 UDS_ARROWKEYS 样式关联的。

## <a name="see-also"></a>请参阅

[使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
