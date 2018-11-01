---
title: 滑块控件成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: 25414b1d98c87c67c1dc8e13bb44bdc25869db94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472639"
---
# <a name="slider-control-member-functions"></a>滑块控件成员函数

应用程序可以调用滑块控件的成员函数以检索有关滑块控件的信息 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 并更改其特征。

若要检索的滑块 （即，用户已选择的值） 的位置，请使用[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成员函数。 若要设置滑块的位置，请使用[SetPos](../mfc/reference/csliderctrl-class.md#setpos)成员函数。 随时可以使用`VerifyPos`成员函数，以确保滑块的最小和最大值之间。

滑块控件的范围是可以表示滑块控件的连续值的集。 大多数应用程序使用[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成员函数首次创建时设置滑块控件的范围。 应用程序可以动态更改范围滑块控件通过使用在创建后[SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax)并[SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin)成员函数。 允许的范围通常动态更改的应用程序检索最后一个范围设置，当用户使用滑块控件处理完。 若要检索这些设置，请使用[GetRange](../mfc/reference/csliderctrl-class.md#getrange)， [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)，并[GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin)成员函数。

应用程序可以使用 TBS_AUTOTICKS 样式有滑块控件的刻度线，将自动显示。 如果应用程序需要控制的位置或刻度线的频率，但是，可以使用多个成员函数。

若要设置刻度线的位置，应用程序可以使用[SetTic](../mfc/reference/csliderctrl-class.md#settic)成员函数。 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)成员函数，应用程序可以设置刻度线显示在固定的时间间隔滑块控件的范围内的标记。 例如，应用程序可以使用此成员函数以显示 1 到 100 之间的范围中只有 10 个刻度。

若要检索对应的刻度的范围中的索引，请使用[GetTic](../mfc/reference/csliderctrl-class.md#gettic)成员函数。 [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray)成员函数检索这些索引的数组。 若要检索的刻度，在客户端坐标中的位置使用[GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos)成员函数。 应用程序可以使用检索的刻度数[GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics)成员函数。

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics)成员函数将移除所有滑块控件的刻度线。

滑块控件的行大小确定应用程序收到 TB_LINEDOWN 或 TB_LINEUP 通知消息时，滑块的移动距离。 同样，页大小确定对 TB_PAGEDOWN 和 TB_PAGEUP 通知消息的响应。 应用程序可以检索并通过设置行和页大小值[GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize)， [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize)， [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)，和[SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize)成员函数。

应用程序可以使用成员函数来检索滑块控件的尺寸。 [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect)成员函数将检索滑块的边界矩形。 [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect)成员函数将检索滑块控件的通道的边界矩形。 （通道是区域通过将滑块移动和选择范围时，其中包含突出显示。）

如果滑块控件具有 TBS_ENABLESELRANGE 样式，用户可以从中选择一系列连续值。 多个成员函数允许动态调整的选择范围。 [SetSelection](../mfc/reference/csliderctrl-class.md#setselection)成员函数设置的起始和结束位置的选择内容。 应用程序时用户已完成设置选择范围，可以使用检索设置[GetSelection](../mfc/reference/csliderctrl-class.md#getselection)成员函数。 若要清除用户的选择，请使用[ClearSel](../mfc/reference/csliderctrl-class.md#clearsel)成员函数。

## <a name="see-also"></a>请参阅

[使用 CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

