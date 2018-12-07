---
title: PAINTSTRUCT 结构
ms.date: 11/04/2016
f1_keywords:
- PAINTSTRUCT
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
ms.openlocfilehash: f1b901ef26c61adbedb3bbe56808cd94bdfad30d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694642"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 结构

`PAINTSTRUCT`结构包含可用于绘制的窗口工作区的信息。

## <a name="syntax"></a>语法

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>参数

*hdc*<br/>
标识要用于绘制的显示上下文。

*fErase*<br/>
指定是否需要重新绘制背景。 它不是 0，如果应用程序应重绘后台。 应用程序负责绘制背景，如果没有背景画笔的情况下创建一个 Windows 窗口类 (请参阅的说明`hbrBackground`的成员[WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) Windows SDK 中的结构)。

*rcPaint*<br/>
指定右上角和右下角的绘制请求在其中的矩形。

*fRestore*<br/>
保留的成员。 它是由 Windows 在内部使用。

*fIncUpdate*<br/>
保留的成员。 它是由 Windows 在内部使用。

*rgbReserved [16]*<br/>
保留的成员。 保留的由 Windows 在内部使用的内存块。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

