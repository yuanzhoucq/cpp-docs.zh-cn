---
title: 使用滑块控件
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: b358b4e92c7d9f214291b047a080f71b48183519
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411508"
---
# <a name="using-slider-controls"></a>使用滑块控件

滑块控件的典型用法遵循以下模式：

- 创建滑块控件。 如果滑块控件是在对话框模板中指定的，则在创建对话框时自动进行创建。 (您应该[CSliderCtrl](../mfc/reference/csliderctrl-class.md)对应于滑块控件在对话框类中的成员。)或者，可以使用[创建](../mfc/reference/csliderctrl-class.md#create)成员函数来创建控件用作子窗口的任何窗口。

- 调用各种 Set 成员函数来设置滑块控件的值。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。 对于控件在对话框中，执行此操作的好时机是在对话框的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数。

- 当用户与该控件交互时，将发送各种通知消息。 可以从控件提取滑动条的值，通过调用[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成员函数。

- 在使用完该控件之后，您需要确保将其正确地销毁。 如果滑块控件在对话框中，将自动销毁该控件和 `CSliderCtrl` 对象。 否则，您需要确保正确地销毁控件和 `CSliderCtrl` 对象。

## <a name="see-also"></a>请参阅

[使用 CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
