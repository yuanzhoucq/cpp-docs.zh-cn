---
title: CREATESTRUCT 结构
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 1de42ba3e26f7a06918a69358083e68f142836cc
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694694"
---
# <a name="createstruct-structure"></a>CREATESTRUCT 结构

`CREATESTRUCT`结构定义传递给应用程序的窗口过程的初始化参数。

## <a name="syntax"></a>语法

```
typedef struct tagCREATESTRUCT {
    LPVOID lpCreateParams;
    HANDLE hInstance;
    HMENU hMenu;
    HWND hwndParent;
    int cy;
    int cx;
    int y;
    int x;
    LONG style;
    LPCSTR lpszName;
    LPCSTR lpszClass;
    DWORD dwExStyle;
} CREATESTRUCT;
```

#### <a name="parameters"></a>参数

*lpCreateParams*<br/>
指向要用于创建窗口的数据。

*hInstance*<br/>
标识拥有新的窗口中的模块的模块实例句柄。

*hMenu*<br/>
标识要由新的窗口的菜单。 如果子窗口中，将包含整数 id。

*hwndParent*<br/>
标识拥有新的窗口的窗口。 如果新窗口是一个顶级窗口，此成员为 NULL。

*cy*<br/>
指定新的窗口的高度。

*cx*<br/>
指定新的窗口的宽度。

*y*<br/>
指定新的窗口的左上角的 y 坐标。 在新窗口是子窗口; 如果坐标是相对于父窗口否则坐标是相对于屏幕源。

*x*<br/>
指定新的窗口的左上角的 x 坐标。 在新窗口是子窗口; 如果坐标是相对于父窗口否则坐标是相对于屏幕源。

*style*<br/>
指定新的窗口[样式](../../mfc/reference/styles-used-by-mfc.md)。

*lpszName*<br/>
指向一个以 null 结尾的字符串，指定新窗口的名称。

*lpszClass*<br/>
指向一个以 null 结尾的字符串，指定新窗口的 Windows 类名称 ( [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)结构; 有关详细信息，请参阅 Windows SDK)。

*dwExStyle*<br/>
指定[扩展样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)新窗口。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

