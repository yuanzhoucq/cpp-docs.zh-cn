---
title: LOGBRUSH 结构
ms.date: 11/04/2016
f1_keywords:
- LOGBRUSH
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
ms.openlocfilehash: 0ca635690843c6dae9db05b0a8cc246cf38ce814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579762"
---
# <a name="logbrush-structure"></a>LOGBRUSH 结构

`LOGBRUSH`结构定义样式、 颜色和物理画笔的模式。 它由 Windows [CreateBrushIndirect](/windows/desktop/api/wingdi/nf-wingdi-createbrushindirect)并[ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)函数。

## <a name="syntax"></a>语法

```
typedef struct tag LOGBRUSH { /* lb */
    UINT lbStyle;
    COLORREF lbColor;
    LONG lbHatch;
} LOGBRUSH;
```

#### <a name="parameters"></a>参数

*lbStyle*<br/>
指定画笔样式。 `lbStyle`成员必须是以下样式之一：

- BS_DIBPATTERN 一个模式画笔由独立于设备的位图 (DIB) 规范的定义。 如果*lbStyle*是 BS_DIBPATTERN，`lbHatch`成员包含的句柄已打包 DIB。

- BS_DIBPATTERNPT 一个模式画笔由独立于设备的位图 (DIB) 规范的定义。 如果*lbStyle*是 BS_DIBPATTERNPT，`lbHatch`成员包含一个指向已打包 DIB。

- BS_HATCHED 影线画笔。

- 空心 BS_HOLLOW 画笔。

- BS_NULL BS_HOLLOW 与相同。

- BS_PATTERN 模式定义的内存位图画笔。

- BS_SOLID 实心画笔。

*lbColor*<br/>
指定是用来绘制画笔的颜色。 如果*lbStyle*是 BS_HOLLOW 或 BS_PATTERN 样式*lbColor*将被忽略。 如果*lbStyle* BS_DIBPATTERN 或 BS_DIBPATTERNBT，低序位字*lbColor*指定是否`bmiColors`成员[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)结构到目前已实现的逻辑调色板中包含显式的红色、 绿色、 蓝色 (RGB) 值或索引。 `lbColor`成员必须是以下值之一：

- DIB_PAL_COLORS 颜色表由向当前已实现的逻辑调色板的 16 位索引的数组。

- DIB_RGB_COLORS 颜色表包含文本的 RGB 值。

*lbHatch*<br/>
指定阴影样式。 含义取决于所定义的画笔样式*lbStyle*。 如果*lbStyle*是 BS_DIBPATTERN，`lbHatch`成员包含的句柄已打包 DIB。 如果*lbStyle*是 BS_DIBPATTERNPT，`lbHatch`成员包含一个指向已打包 DIB。 如果*lbStyle*是 BS_HATCHED，`lbHatch`成员指定用于创建阴影的行的方向。 它可以是下列值之一：

- HS_BDIAGONAL 的 45 度向上、 从左到右阴影

- HS_CROSS 水平和垂直交叉影线

- HS_DIAGCROSS 45 度交叉影线

- HS_FDIAGONAL 的 45 度向下、 从左到右阴影

- HS_HORIZONTAL 水平阴影

- HS_VERTICAL 垂直阴影

如果*lbStyle*是 BS_PATTERN， *lbHatch*是定义的模式的位图的句柄。 如果*lbStyle* BS_SOLID 或 BS_HOLLOW， *lbHatch*将被忽略。

## <a name="remarks"></a>备注

尽管*lbColor*控制阴影画笔的前景色[CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode)并[CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor)函数控制的背景色。

## <a name="requirements"></a>要求

**标头：** wingdi.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

