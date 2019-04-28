---
title: 调节按钮样式
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: d955ba1d76ee4d5648613ddaf6c5f6a652f3d3af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307167"
---
# <a name="spin-button-styles"></a>调节按钮样式

调节按钮的设置的许多 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) 由样式控制。 可以设置以下使用的样式**属性**对话框编辑器中的窗口。

- **方向**垂直或水平。 控件的方向箭头按钮。 与 UDS_HORZ 样式相关联。

- **对齐方式**之一未附加、 左侧或右侧。 控制数值调节钮的位置。 左侧和右侧置于调节按钮旁合作者窗口。 减小合作者窗口的宽度以适应数值调节按钮。 与 UDS_ALIGNLEFT 和 UDS_ALIGNRIGHT 样式相关联。

- **Auto Buddy** Z 顺序中的上一个窗口会自动选择为数值调节钮的合作者窗口。 在对话框模板中，这是之前的 tab 键顺序的数值调节钮的控件。 与 UDS_AUTOBUDDY 样式相关联。

- **设置 Buddy Integer**导致数值调节钮控件进行递增和递减当前的位置更改作为合作者窗口的标题。 与 UDS_SETBUDDYINT 样式相关联。

- **没有千位**不会插入千位分隔符在合作者窗口的标题中的值。 与 UDS_NOTHOUSANDS 样式相关联。

    > [!NOTE]
    >  如果你想要使用对话框数据交换 (DDX) 从合作者控件获取的整数值，请设置此样式。 `DDX_Text` 不接受嵌入千位分隔符。

- **包装**会导致"包装"由于值是递增或递减的控制范围之外的位置。 与 UDS_WRAP 样式相关联。

- **箭头键**导致调节按钮要递增或递减位置按向上键和向下箭头键时。 与 UDS_ARROWKEYS 样式相关联。

## <a name="see-also"></a>请参阅

[使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
