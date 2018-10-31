---
title: POINT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- POINT
- LPPOINT
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2aaafe65b742ded6c0adf49fac430679e24380
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334504"
---
# <a name="point-structure"></a>POINT 结构

`POINT`结构定义 x*-* 和点的 y 坐标。

## <a name="syntax"></a>语法

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>参数

*x*<br/>
指定一个点的 x 坐标。

*y*<br/>
指定一个点的 y 坐标。

## <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>要求

**标头：** windef.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)
