---
title: 选项卡和选项卡控件特性
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511241"
---
# <a name="tabs-and-tab-control-attributes"></a>选项卡和选项卡控件特性

您对构成选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 的选项卡的外观和行为具有相当大的控制权。 每个选项卡可以有一个与之关联的标签、图标、项状态和应用程序定义的32位值。 对于每个选项卡, 可以显示图标和/或标签。

此外, 每个选项卡项可以有三种可能的状态: 按下、unpressed 或突出显示。 仅可通过修改现有选项卡项设置此状态。 若要修改现有选项卡项, 请使用对[GetItem](../mfc/reference/ctabctrl-class.md#getitem)的调用来检索它`TCITEM` , 修改该结构 (特别是*dwState*和*dwStateMask*数据成员), 然后通过`TCITEM`调用返回已修改的结构[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 如果需要清除`CTabCtrl`对象中所有选项卡项的状态, 请调用[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)。 此函数将重置所有选项卡项或所有项 (当前选定项除外) 的状态。

下面的代码清除所有选项卡项的状态, 然后修改第三项的状态:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

有关选项卡属性的详细信息, 请参阅 Windows SDK 中的[选项卡和选项卡属性](/windows/win32/Controls/tab-controls)。 有关将选项卡添加到选项卡控件的详细信息, 请参阅本主题后面的将选项卡[添加到选项卡控件](../mfc/adding-tabs-to-a-tab-control.md)。

## <a name="see-also"></a>请参阅

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
