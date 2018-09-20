---
title: MINMAXINFO 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63589edbe47aa09b8a6be92b5b7eb7e29077c96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402286"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO 结构

`MINMAXINFO`结构包含有关最大化的窗口的大小和位置以及其最小值和最大跟踪大小的信息。

## <a name="syntax"></a>语法

```
typedef struct tagMINMAXINFO {
    POINT ptReserved;
    POINT ptMaxSize;
    POINT ptMaxPosition;
    POINT ptMinTrackSize;
    POINT ptMaxTrackSize;
} MINMAXINFO;
```

#### <a name="parameters"></a>参数

*ptReserved*<br/>
保留以供内部使用。

*ptMaxSize*<br/>
指定的最大化的宽度 (point.x) 和窗口的最大化的高度 (point.y)。

*ptMaxPosition*<br/>
指定左侧和右侧的最大化窗口 (point.x) 的位置和最大化窗口 (point.y) 顶部的位置。

*ptMinTrackSize*<br/>
指定的最小跟踪宽度 (point.x)，最小跟踪窗口的高度 (point.y)。

*ptMaxTrackSize*<br/>
指定跟踪宽度 (point.x) 的最大值和跟踪窗口的高度 (point.y) 的最大值。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

