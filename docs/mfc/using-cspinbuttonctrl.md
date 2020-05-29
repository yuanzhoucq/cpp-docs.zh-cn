---
title: 使用 CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366484"
---
# <a name="using-cspinbuttonctrl"></a>使用 CSpinButtonCtrl

*旋转按钮*控件（也称为*向上向下*控件）提供一对箭头，用户可以单击该箭头来调整值。 此值称为*当前位置*。 此位置位于数值调节钮的范围内。 当用户单击向上箭头，位置将朝着最大值移动；当用户单击向下箭头，位置将朝着最小值移动。

旋转按钮控件由[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)类在 MFC 中表示。

> [!NOTE]
> 默认情况下，数值调节钮的范围最大设置为零 (0)，最小设置为 100。 由于最大值小于最小值，因此单击上箭头将降低位置，单击下箭头将增高位置。 使用[CSpinButtonCtrl：设置范围](../mfc/reference/cspinbuttonctrl-class.md#setrange)来调整这些值。

通常，当前位置显示在附带控件中。 配套控件称为*好友窗口*。 有关旋转按钮控件的说明，请参阅 Windows SDK 中的["向上向下控件](/windows/win32/Controls/up-down-controls)"。

若要在 Visual Studio 中创建数值调节钮控件和编辑控件合作者窗口，请先将编辑控件拖至对话框或窗口，然后拖动数值调节钮控件。 选择旋转控件，并将其**自动好友**和**将好友整数属性设置为** **True**。 还设置**对齐**属性;**右对齐**最典型。 在这些设置中，编辑控件将设置为合作者窗口，因为合作者窗口将直接按选项卡顺序位于编辑控件前。 编辑控件将显示整数，数值调节钮控件将嵌入编辑控件右侧。 或者，您可以使用[CSpinButtonCtrl：setRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)方法设置旋转控件的有效范围。 在数值调节钮控件与合作者窗口之间通信无需任何事件处理程序，因为它们直接交换数据。 如果将自旋控件用于其他目的，例如，通过一系列窗口或对话框进行页面，则为UDN_DELTAPOS消息添加处理程序，并在那里执行自定义操作。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [旋转按钮样式](../mfc/spin-button-styles.md)

- [旋转按钮成员功能](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>另请参阅

[控件](../mfc/controls-mfc.md)
