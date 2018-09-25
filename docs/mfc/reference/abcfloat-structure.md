---
title: ABCFLOAT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375406"
---
# <a name="abcfloat-structure"></a>ABCFLOAT 结构

`ABCFLOAT`结构包含 A、 B 和 C 的字体字符宽度。

## <a name="syntax"></a>语法

```
typedef struct _ABCFLOAT { /* abcf */
    FLOAT abcfA;
    FLOAT abcfB;
    FLOAT abcfC;
} ABCFLOAT;
```

#### <a name="parameters"></a>参数

*abcfA*<br/>
指定字符的 A 间距。 A 间距是在绘制字符标志符号之前要添加到当前位置的距离。

*abcfB*<br/>
指定字符的 B 间距。 B 间距是字符标志符号的绘制部分的宽度。

*abcfC*<br/>
指定字符的 C 间距。 C 间距是要添加到当前位置以便为字符标志符号的右侧提供空白的距离。

## <a name="remarks"></a>备注

A、 B 和 C 宽度为沿基准线的字体的单位。 一个字符的字符增量 （总宽度） 是 A、 B 和 C 空间之和。 A 或 C 间距可以是负值以指示空白部分或延伸量。

## <a name="requirements"></a>要求

**标头：** wingdi.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

