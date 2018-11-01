---
title: LOGPEN 结构
ms.date: 11/04/2016
f1_keywords:
- LOGPEN
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
ms.openlocfilehash: d53d99f5aed0fa0e0a67f829af2b8751d56d492d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589340"
---
# <a name="logpen-structure"></a>LOGPEN 结构

`LOGPEN`结构定义样式、 宽度和颜色的钢笔、 drawing 对象用于绘制线条和边框。 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)函数使用`LOGPEN`结构。

## <a name="syntax"></a>语法

```
typedef struct tagLOGPEN {  /* lgpn */
    UINT lopnStyle;
    POINT lopnWidth;
    COLORREF lopnColor;
} LOGPEN;
```

#### <a name="parameters"></a>参数

*lopnStyle*<br/>
指定的笔类型。 此成员可以是下列值之一：

- PS_SOLID 创建实心笔。

- PS_DASH 创建虚线的笔。 （仅当钢笔的宽度为 1 时有效）。

- PS_DOT 创建以点分隔的笔。 （仅当钢笔的宽度为 1 时有效）。

- 使用替代的笔 PS_DASHDOT 创建短划线和点。 （仅当钢笔的宽度为 1 时有效）。

- PS_DASHDOTDOT 创建一个使用替代的短划线和双点笔的。 （仅当钢笔的宽度为 1 时有效）。

- PS_NULL 创建空的笔。

- PS_INSIDEFRAME 通过 GDI 创建钢笔绘制一条线绘制闭合形状的框架内生成输出指定的绑定矩形的函数 (例如， `Ellipse`， `Rectangle`， `RoundRect`， `Pie`，和`Chord`成员函数）。 此样式时用于 GDI 输出未指定的绑定矩形的函数 (例如，`LineTo`成员函数)，框架不受限制的笔绘制的区域。

   如果笔具有 PS_INSIDEFRAME 样式和颜色的不匹配逻辑的颜色表中的颜色，笔绘制抖色的颜色。 PS_SOLID 笔样式不能用于与抖色创建钢笔。 PS_INSIDEFRAME 样式等同于 PS_SOLID 钢笔的宽度是否小于或等于 1。

   使用 GDI 对象使用 PS_INSIDEFRAME 样式时生成的函数以外`Ellipse`， `Rectangle`，和`RoundRect`，行可能无法完全在指定范围内。

*lopnWidth*<br/>
指定钢笔的宽度，以逻辑单位。 如果`lopnWidth`成员为 0，触笔位于 1 个像素宽而不考虑当前映射模式的光栅设备上。

*lopnColor*<br/>
指定的钢笔颜色。

## <a name="remarks"></a>备注

`y`中的值[点](../../mfc/reference/point-structure1.md)结构`lopnWidth`成员未使用。

## <a name="requirements"></a>要求

**标头：** wingdi.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

