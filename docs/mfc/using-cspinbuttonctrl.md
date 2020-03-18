---
title: 使用 CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 775668426cd11e20a4c863f07a964935d0d5420f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447185"
---
# <a name="using-cspinbuttonctrl"></a>使用 CSpinButtonCtrl

*数值调节钮*控件（也称为*up-down 控件）* 提供了一对箭头，用户可以单击该箭头调整值。 此值称为*当前位置*。 此位置位于数值调节钮的范围内。 当用户单击向上箭头，位置将朝着最大值移动；当用户单击向下箭头，位置将朝着最小值移动。

数值调节钮控件在 MFC 中由[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)类表示。

> [!NOTE]
>  默认情况下，数值调节钮的范围最大设置为零 (0)，最小设置为 100。 由于最大值小于最小值，因此单击上箭头将降低位置，单击下箭头将增高位置。 使用[CSpinButtonCtrl：： SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)调整这些值。

通常，当前位置显示在附带控件中。 伴生控制称为 "合作者"*窗口*。 有关数值调节钮控件的图例，请参阅[关于](/windows/win32/Controls/up-down-controls)Windows SDK 中的 up-down 控件。

若要在 Visual Studio 中创建数值调节钮控件和编辑控件合作者窗口，请先将编辑控件拖至对话框或窗口，然后拖动数值调节钮控件。 选择旋转控件并设置其**自动合作者**，并将**合作者整数属性设置**为**True**。 同时设置**对齐方式**属性;最常见的情况是**右对齐**。 在这些设置中，编辑控件将设置为合作者窗口，因为合作者窗口将直接按选项卡顺序位于编辑控件前。 编辑控件将显示整数，数值调节钮控件将嵌入编辑控件右侧。 或者，您可以使用[CSpinButtonCtrl：： SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)方法设置数值调节钮控件的有效范围。 在数值调节钮控件与合作者窗口之间通信无需任何事件处理程序，因为它们直接交换数据。 例如，如果您将自旋控件用于其他目的（例如，要逐页浏览一系列窗口或对话框），请为 UDN_DELTAPOS 消息添加处理程序，并在其中执行自定义操作。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [调节按钮样式](../mfc/spin-button-styles.md)

- [调节按钮成员函数](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>另请参阅

[控件](../mfc/controls-mfc.md)
