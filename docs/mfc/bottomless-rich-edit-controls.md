---
title: 无界限 Rich Edit 控件
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 6f078680777dcf80a4349ea34e4520cb56031f44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400742"
---
# <a name="bottomless-rich-edit-controls"></a>无界限 Rich Edit 控件

你的应用程序可以调整 rich edit 控件的大小 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 根据需要以便它始终是其内容的大小相同。 Rich edit 控件支持此所谓的"无限制"功能通过发送其父窗口[EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize)通知消息的内容大小发生更改时。

处理时**EN_REQUESTRESIZE**通知消息，应用程序应调整大小的尺寸以指定的控件[REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize)结构。 应用程序可能也会移动控件附近的任何信息，以适应控件的高度变化。 若要调整控件的大小，可以使用`CWnd`函数[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。

您可以强制无界限 rich edit 控件发送**EN_REQUESTRESIZE**使用的通知消息[RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize)成员函数。 此消息很有用[OnSize](../mfc/reference/cwnd-class.md#onsize)处理程序。

若要接收**EN_REQUESTRESIZE**通知消息，必须启用通知，可以使用`SetEventMask`成员函数。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
