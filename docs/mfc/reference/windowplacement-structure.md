---
title: WINDOWPLACEMENT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b163d93de22d313d72ca5dbfd384788077ae1b01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447267"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT 结构

`WINDOWPLACEMENT`结构包含在屏幕上的一个窗口的布局信息。

## <a name="syntax"></a>语法

```
typedef struct tagWINDOWPLACEMENT {     /* wndpl */
    UINT length;
    UINT flags;
    UINT showCmd;
    POINT ptMinPosition;
    POINT ptMaxPosition;
    RECT rcNormalPosition;
} WINDOWPLACEMENT;
```

#### <a name="parameters"></a>参数

*length*<br/>
指定的长度以字节为单位的结构。

*flags*<br/>
指定用于控制最小化的窗口和窗口还原所依据的方法的位置的标志。 此成员可以是一个或两个下列标志：

- WPF_SETMINPOSITION 指定可以指定将 x 的位置和 y 的位置的最小化窗口。 此标志必须为指定是否坐标在设置`ptMinPosition`成员。

- WPF_RESTORETOMAXIMIZED 指定的还原窗口将最大化，而不考虑是否它已最大化之前被最小化。 此设置为有效仅还原窗口的下一次。 它不会更改默认还原行为。 仅当指定 SW_SHOWMINIMIZED 值时，此标志才有效`showCmd`成员。

*showCmd*<br/>
指定窗口的当前显示状态。 此成员可以是下列值之一：

- SW_HIDE 隐藏窗口，并将激活传递到另一个窗口。

- SW_MINIMIZE 最大程度减少指定的窗口，并激活系统的列表中的顶级窗口。

- SW_RESTORE 激活并显示的窗口。 如果最小化或最大化窗口，Windows 会将其还原到其原始大小和位置 （与 SW_SHOWNORMAL 相同）。

- SW_SHOW 激活一个窗口，并将其显示在其当前大小和位置。

- SW_SHOWMAXIMIZED 激活一个窗口，并将其显示为最大化窗口。

- SW_SHOWMINIMIZED 激活一个窗口，并将其显示为一个图标。

- SW_SHOWMINNOACTIVE 以图标形式显示一个窗口。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNA 显示在其当前状态的窗口。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNOACTIVATE 显示一个窗口中的最新的大小和位置。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNORMAL 激活并显示的窗口。 如果最小化或最大化窗口，Windows 会将其还原到其原始大小和位置 （为 SW_RESTORE 相同）。

*ptMinPosition*<br/>
在窗口最小化时指定窗口的左上角的位置。

*ptMaxPosition*<br/>
最大化窗口时，请指定窗口的左上角的位置。

*rcNormalPosition*<br/>
当窗口处于正常 （已还原） 的位置，请指定窗口的坐标。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

