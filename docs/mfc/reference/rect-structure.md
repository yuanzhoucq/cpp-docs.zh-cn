---
title: RECT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae2b248f4aa4586bf6453dcc37b521387327d25
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334515"
---
# <a name="rect-structure"></a>RECT 结构

`RECT` 结构定义矩形左上角和右下角的坐标。

## <a name="syntax"></a>语法

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>成员

`left`<br/>
指定矩形左上角的 x 坐标。

`top`<br/>
指定矩形左上角的 y 坐标。

`right`<br/>
指定矩形右下角的 x 坐标。

`bottom`<br/>
指定矩形右下角的 y 坐标。

## <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>要求

**标头：** windef.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)
