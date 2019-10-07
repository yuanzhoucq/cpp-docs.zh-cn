---
title: 无界限 Rich Edit 控件
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 4affdbeed723ea83beda785116dc4c45771073b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509146"
---
# <a name="bottomless-rich-edit-controls"></a>无界限 Rich Edit 控件

应用程序可以根据需要调整多格式编辑控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 的大小, 使其大小始终与内容相同。 Rich edit 控件支持此名为 "无限" 的功能, 方法是在其内容大小发生更改时, 向其父窗口发送[EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize)通知消息。

处理**EN_REQUESTRESIZE**通知消息时, 应用程序应将控件的大小调整为指定的[REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize)结构中的维度。 应用程序可能也会移动控件附近的任何信息，以适应控件的高度变化。 若要调整控件的大小, 可以使用`CWnd`函数[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。

可以使用[REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize)成员函数强制无限 rich edit 控件发送**EN_REQUESTRESIZE**通知消息。 此消息在[OnSize](../mfc/reference/cwnd-class.md#onsize)处理程序中很有用。

若要接收**EN_REQUESTRESIZE**通知消息, 必须使用`SetEventMask`成员函数启用通知。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
