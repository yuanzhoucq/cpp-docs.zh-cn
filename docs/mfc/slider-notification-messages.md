---
title: 滑块通知消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b003e23a1fef2b44600b9fd15dfe4ca541df5369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381974"
---
# <a name="slider-notification-messages"></a>滑块通知消息
滑块控件将通过发送父来通知用户操作其父窗口`WM_HSCROLL`或`WM_VSCROLL`消息，具体取决于滑块控件的方向。 若要处理这些消息，请添加处理程序`WM_HSCROLL`和`WM_VSCROLL`向父窗口的消息。 [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../mfc/reference/cwnd-class.md#onvscroll)通知代码、 滑块和指向的指针的位置，则成员函数将传递[CSliderCtrl](../mfc/reference/csliderctrl-class.md)对象。 请注意，指针为类型**CScrollBar \*** 即使它指向`CSliderCtrl`对象。 你可能需要转换此指针，如果你需要操作滑块控件。  
  
 而不是使用滚动条通知代码，滑块控件将发送一组不同的通知代码。 滑块控件将发送**TB_BOTTOM**， **TB_LINEDOWN**， **TB_LINEUP**，和**TB_TOP**通知代码仅在用户交互时使用通过使用键盘的滑块控件。 **TB_THUMBPOSITION**和**TB_THUMBTRACK**用户使用鼠标时仅发送通知消息。 **TB_ENDTRACK**， **TB_PAGEDOWN**，和**TB_PAGEUP**两种情况下发送通知代码。  
  
 下表列出滑块控件通知消息和导致发送通知的事件 （虚拟键代码或鼠标事件）。 （有关标准虚拟键代码的列表，请参见 Winuser.h。）  
  
|通知消息|导致发送通知的事件|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP` （用户发布发送相关的虚拟键代码的密钥）|  
|**TB_LINEDOWN**|**VK_RIGHT**或**VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT**或**VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** （用户单击下方或右侧的滑块的通道）|  
|**TB_PAGEUP**|**VK_PRIOR** （用户单击通道的上方或左侧的滑块）|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP` 以下**TB_THUMBTRACK**通知消息|  
|**TB_THUMBTRACK**|（用户通过拖动滑块） 的滑块移动|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)

