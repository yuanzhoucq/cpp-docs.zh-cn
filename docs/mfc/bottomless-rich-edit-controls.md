---
title: 无界限 Rich Edit 控件
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 567bb5b7f2eb2c203b40b9f1f6add82f5451d672
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616424"
---
# <a name="bottomless-rich-edit-controls"></a>无界限 Rich Edit 控件

应用程序可以根据需要调整多格式编辑控件（[CRichEditCtrl](reference/cricheditctrl-class.md)）的大小，使其大小始终与内容相同。 Rich edit 控件支持此名为 "无限" 的功能，方法是在其内容大小发生更改时，向其父窗口发送[EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize)通知消息。

当处理**EN_REQUESTRESIZE**通知消息时，应用程序应将控件调整为指定[REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize)结构中的维度。 应用程序可能也会移动控件附近的任何信息，以适应控件的高度变化。 若要调整控件的大小，可以使用 `CWnd` 函数[SetWindowPos](reference/cwnd-class.md#setwindowpos)。

可以通过使用[REQUESTRESIZE](reference/cricheditctrl-class.md#requestresize)成员函数强制无限 rich edit 控件发送**EN_REQUESTRESIZE**通知消息。 此消息在[OnSize](reference/cwnd-class.md#onsize)处理程序中很有用。

若要接收**EN_REQUESTRESIZE**通知消息，必须使用 `SetEventMask` 成员函数启用通知。

## <a name="see-also"></a>另请参阅

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控件](controls-mfc.md)
