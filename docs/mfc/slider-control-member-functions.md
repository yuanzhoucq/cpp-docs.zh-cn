---
title: 滑块控件成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14e6df9a5d4dc6631b6891f90b55b63b73989b30
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953953"
---
# <a name="slider-control-member-functions"></a>滑块控件成员函数
应用程序可以调用滑块控件的成员函数来检索滑块控件有关的信息 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 并更改其特征。  
  
 若要检索的滑块 （即，用户已选择的值） 的位置，请使用[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成员函数。 若要设置滑块的位置，请使用[SetPos](../mfc/reference/csliderctrl-class.md#setpos)成员函数。 在任何时候，你可以使用`VerifyPos`成员函数，以确保滑块的最小和最大值之间。  
  
 滑块控件的范围是可以表示滑块控件的连续值的集。 大多数应用程序使用[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成员函数首次创建时设置滑块控件的范围。 应用程序可以动态更改范围后已通过使用创建滑块控件[SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax)和[SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin)成员函数。 允许范围内动态通常更改应用程序检索的最后一个范围设置，用户完成后使用滑块控件。 若要检索这些设置，请使用[GetRange](../mfc/reference/csliderctrl-class.md#getrange)， [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)，和[GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin)成员函数。  
  
 应用程序可以使用 TBS_AUTOTICKS 样式让滑块控件的刻度线，将自动显示。 如果应用程序需要控制的位置或刻度线的频率，但是，可以使用大量的成员函数。  
  
 若要设置刻度线的位置，应用程序可以使用[SetTic](../mfc/reference/csliderctrl-class.md#settic)成员函数。 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)成员函数允许应用程序设置滑块控件的范围中的定期出现的标记的刻度线。 例如，应用程序可以使用此成员函数以显示 1 到 100 之间的一系列中只有 10 个刻度线。  
  
 若要检索对应的刻度线的范围中的索引，使用[GetTic](../mfc/reference/csliderctrl-class.md#gettic)成员函数。 [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray)成员函数检索这些索引的数组。 若要检索的位置为刻度线，在客户端坐标中，使用[GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos)成员函数。 应用程序可以使用检索的刻度数[GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics)成员函数。  
  
 [ClearTics](../mfc/reference/csliderctrl-class.md#cleartics)成员函数中移除所有滑块控件的刻度线。  
  
 滑块控件的行大小确定当应用程序收到 TB_LINEDOWN 或 TB_LINEUP 通知消息滑块移动的距离。 同样，页面大小确定对 TB_PAGEDOWN 和 TB_PAGEUP 通知消息的响应。 应用程序可以检索并通过设置行和页大小值[GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize)， [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize)， [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)，和[SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize)成员函数。  
  
 应用程序可以使用成员函数检索滑块控件的维度。 [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect)成员函数将检索滑块的绑定矩形。 [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect)成员函数将检索滑块控件的通道的绑定矩形。 （通道高于区域滑块而移动和选择范围时，其中包含突出显示。）  
  
 如果滑块控件具有 TBS_ENABLESELRANGE 样式，用户可以从它选择连续值的范围。 大量的成员函数允许动态调整选择范围。 [SetSelection](../mfc/reference/csliderctrl-class.md#setselection)成员函数设置的起始和结束的选择内容的位置。 应用程序时用户已完成设置选择范围，可以通过使用来检索设置[GetSelection](../mfc/reference/csliderctrl-class.md#getselection)成员函数。 若要清除用户的选择，请使用[ClearSel](../mfc/reference/csliderctrl-class.md#clearsel)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)

