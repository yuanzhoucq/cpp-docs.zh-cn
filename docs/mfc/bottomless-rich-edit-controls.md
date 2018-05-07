---
title: 无界限 Rich Edit 控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2b08f6c04d345b4ae3ab32c6d0f17a1d8a4647
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="bottomless-rich-edit-controls"></a>无界限 Rich Edit 控件
你的应用程序可以调整 rich edit 控件的大小 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 根据需要以便它始终是相同的大小及其内容。 Rich edit 控件支持此所谓的"无界限"功能通过发送其父窗口[EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983)其内容的大小发生更改时的通知消息。  
  
 在处理时**EN_REQUESTRESIZE**通知消息，应用程序应调整大小的控件中指定的维度[REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950)结构。 应用程序可能也会移动控件附近的任何信息，以适应控件的高度变化。 若要调整控件的大小，可以使用`CWnd`函数[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 你可以强制无界限 rich edit 控件发送**EN_REQUESTRESIZE**使用的通知消息[RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize)成员函数。 此消息中会很有用[OnSize](../mfc/reference/cwnd-class.md#onsize)处理程序。  
  
 若要接收**EN_REQUESTRESIZE**通知消息，你必须通过使用启用通知`SetEventMask`成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

