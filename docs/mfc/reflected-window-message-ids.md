---
title: 反射窗口消息 Id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
dev_langs:
- C++
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac529c3084917bd43fbb0a9fd51f1f0e3942447b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416015"
---
# <a name="reflected-window-message-ids"></a>反射窗口消息 ID

一种快速创建 ActiveX 控件或其他专用控件的方法是子类化窗口。 有关详细信息，请参阅[MFC ActiveX 控件： 子类化 Windows 控件](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

若要防止控件的容器接收由子类化 Windows 控件，发送的窗口消息[COleControl](../mfc/reference/colecontrol-class.md)创建"reflector"窗口来截获某些窗口消息并将其发送回控件。 控件在其窗口过程中可以通过对 ActiveX 控件采取适当操作来处理这些反射的消息。

下表显示了截获的消息和反射器窗口发送的相应消息。

|控件发送的消息|发射到控件的消息|
|---------------------------------|--------------------------------------|
|[WM_COMMAND](/windows/desktop/menurc/wm-command)|OCM_COMMAND|
|[WM_CTLCOLORBTN](/windows/desktop/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|
|[WM_CTLCOLOREDIT](/windows/desktop/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|
|[WM_CTLCOLORDLG](/windows/desktop/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|
|[WM_CTLCOLORLISTBOX](/windows/desktop/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|
|[WM_CTLCOLORSCROLLBAR](/windows/desktop/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|
|[WM_CTLCOLORSTATIC](/windows/desktop/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|
|[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)|OCM_DRAWITEM|
|[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)|OCM_MEASUREITEM|
|[WM_DELETEITEM](/windows/desktop/Controls/wm-deleteitem)|OCM_DELETEITEM|
|[WM_VKEYTOITEM](/windows/desktop/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|
|[WM_CHARTOITEM](/windows/desktop/Controls/wm-chartoitem)|OCM_CHARTOITEM|
|[WM_COMPAREITEM](/windows/desktop/Controls/wm-compareitem)|OCM_COMPAREITEM|
|[WM_HSCROLL](/windows/desktop/Controls/wm-hscroll)|OCM_HSCROLL|
|[WM_VSCROLL](/windows/desktop/Controls/wm-vscroll)|OCM_VSCROLL|
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|
|[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)|OCM_NOTIFY|

> [!NOTE]
>  如果控件在 Win32 系统上运行，有几种类型的 WM_CTLCOLOR\*可能会收到的消息。 有关详细信息，请参阅 WM_CTLCOLORBTN、 WM_CTLCOLORDLG、 WM_CTLCOLOREDIT、 WM_CTLCOLORLISTBOX、 WM_CTLCOLORMSGBOX、 WM_CTLCOLORSCROLLBAR、 WM_CTLCOLORSTATIC。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：创建 Windows 控件的子类](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[TN062：Windows 控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)

