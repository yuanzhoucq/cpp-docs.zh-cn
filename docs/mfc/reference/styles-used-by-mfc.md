---
title: "MFC 使用的样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.styles
dev_langs:
- C++
helpviewer_keywords:
- edit styles [MFC]
- window styles, in MFC
- styles
- frame windows, styles
- message-box styles
- styles, MFC
- buttons, MFC toolbars
- list boxes, styles
- static styles
- scroll-bar styles [MFC]
- combo boxes, styles
- extended window styles
ms.assetid: d3b9af37-31b5-4c97-a8ad-189fd724b04c
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 344d2ce3de15403e17f29dc9504253cbb0ade607
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="styles-used-by-mfc"></a>MFC 使用的样式
在创建对应的 MFC 对象时，请使用以下的样式。 在大多数情况下，这些样式中设置`dwStyle`类参数**创建**函数。  
  
### <a name="mfc-styles"></a>MFC 样式  
  
|样式|说明|  
|-----------|-----------------|  
|[按钮样式](../../mfc/reference/button-styles.md)|适用于[CButton 类](../../mfc/reference/cbutton-class.md)对象，如单选按钮、 复选框和按钮。 指定的中的样式组合`dwStyle`参数[CButton::Create](../../mfc/reference/cbutton-class.md#create)。|  
|[组合框样式](../../mfc/reference/combo-box-styles.md)|适用于[CComboBox 类](../../mfc/reference/ccombobox-class.md)对象。 指定的中的样式组合`dwStyle`参数[CComboBox::Create](../../mfc/reference/ccombobox-class.md#create)。|  
|[编辑样式](../../mfc/reference/edit-styles.md)|适用于[CEdit 类](../../mfc/reference/cedit-class.md)对象。 指定的中的样式组合`dwStyle`参数[CEdit::Create](../../mfc/reference/cedit-class.md#create)。|  
|[框架窗口样式](../../mfc/reference/frame-window-styles-mfc.md)|适用于[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)对象。 指定的中的样式组合`dwStyle`参数[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)。|  
|[列表框样式](../../mfc/reference/list-box-styles.md)|适用于[CListBox 类](../../mfc/reference/clistbox-class.md)对象。 指定的中的样式组合`dwStyle`参数[CListBox::Create](../../mfc/reference/clistbox-class.md#create)。|  
|[消息框样式](../../mfc/reference/message-box-styles.md)|适用于[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)项。 指定的中的样式组合`nType`参数`AfxMessageBox`。|  
|[滚动条样式](../../mfc/reference/scroll-bar-styles.md)|适用于[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)对象。 指定的中的样式组合`dwStyle`参数[CScrollBar::Create](../../mfc/reference/cscrollbar-class.md#create)。|  
|[静态样式](../../mfc/reference/static-styles.md)|适用于[CStatic 类](../../mfc/reference/cstatic-class.md)对象。 指定的中的样式组合`dwStyle`参数[CStatic::Create](../../mfc/reference/cstatic-class.md#create)。|  
|[窗口样式](../../mfc/reference/window-styles.md)|适用于[CWnd 类](../../mfc/reference/cwnd-class.md)对象。 指定的中的样式组合`dwStyle`参数[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)。|  
|[扩展的窗口样式](../../mfc/reference/extended-window-styles.md)|适用于[CWnd 类](../../mfc/reference/cwnd-class.md)对象。 指定的中的样式组合`dwExStyle`参数[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)。|  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../mfc/class-library-overview.md)


