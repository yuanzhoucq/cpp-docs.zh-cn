---
title: ABCFLOAT 结构
ms.date: 11/04/2016
f1_keywords:
- ABCFLOAT
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
ms.openlocfilehash: b9e3923e8c70e38fe5efe959db8da43118cc6445
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443650"
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

