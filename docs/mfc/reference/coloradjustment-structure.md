---
title: COLORADJUSTMENT 结构
ms.date: 11/04/2016
f1_keywords:
- COLORADJUSTMENT
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
ms.openlocfilehash: 4f25b8241c1862a9c12d405ee5d47d5553dd6e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623504"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT 结构

`COLORADJUSTMENT`结构定义使用 Windows 的颜色调整值`StretchBlt`并`StretchDIBits`函数时`StretchBlt`模式是半色调。

## <a name="syntax"></a>语法

```
typedef struct  tagCOLORADJUSTMENT {    /* ca */
    WORD caSize;
    WORD caFlags;
    WORD caIlluminantIndex;
    WORD caRedGamma;
    WORD caGreenGamma;
    WORD caBlueGamma;
    WORD caReferenceBlack;
    WORD caReferenceWhite;
    SHORT caContrast;
    SHORT caBrightness;
    SHORT caColorfulness;
    SHORT caRedGreenTint;
} COLORADJUSTMENT;
```

#### <a name="parameters"></a>参数

*caSize*<br/>
以字节为单位指定结构的大小。

*caFlags*<br/>
指定输出图像应做好准备。 此成员可以设置为 NULL 或以下值的任意组合：

- CA_NEGATIVE 指定应显示原始图像的负值。

- CA_LOG_FILTER 指定对数函数，应应用于最终输出颜色的密度。 亮度较低时，这会增加的颜色对比度。

*caIlluminantIndex*<br/>
指定图像对象查看其下的光源的亮度。 此成员可以设置为以下值之一：

- ILLUMINANT_EQUAL_ENERGY

- ILLUMINANT_A

- ILLUMINANT_B

- ILLUMINANT_C

- ILLUMINANT_D50

- ILLUMINANT_D55

- ILLUMINANT_D65

- ILLUMINANT_D75

- ILLUMINANT_F2

- ILLUMINANT_TURNGSTEN

- ILLUMINANT_DAYLIGHT

- ILLUMINANT_FLUORESCENT

- ILLUMINANT_NTSC

*caRedGamma*<br/>
指定源颜色的红色主的 n 次幂灰度校正值。 值必须介于 2,500 65000。 值为 10000 表示没有灰度校正。

*caGreenGamma*<br/>
指定源颜色的绿色主的 n 次幂灰度校正值。 值必须介于 2,500 65000。 值为 10000 表示没有灰度校正。

*caBlueGamma*<br/>
指定源色蓝原色的 n 次幂灰度校正值。 值必须介于 2,500 65000。 值为 10000 表示没有灰度校正。

*caReferenceBlack*<br/>
指定源颜色为黑色的引用。 比这更深的任何颜色将被视为黑色。 值必须介于 0 到 4000。

*caReferenceWhite*<br/>
指定源色为白色的引用。 比这更亮的任何颜色将被视为空白。 值必须介于 6,000 为 10,000。

*caContrast*<br/>
指定要应用于源对象的对比度的量。 值必须为介于-100 到 100 之间。 值为 0 表示没有对比度调整。

*caBrightness*<br/>
指定要应用于源对象的亮度。 值必须为介于-100 到 100 之间。 值为 0 表示没有亮度调整。

*caColorfulness*<br/>
指定要应用于源对象的 colorfulness 量。 值必须为介于-100 到 100 之间。 值为 0 表示不做任何 colorfulness 调整。

*caRedGreenTint*<br/>
指定要应用于源对象的红色或绿色色调调整的量。 值必须为介于-100 到 100 之间。 正数会调整针对红色并负数调整针对绿色。 0 表示不做任何色调调整。

## <a name="requirements"></a>要求

**标头：** wingdi.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)

