---
title: XFORM 结构
ms.date: 11/04/2016
f1_keywords:
- XFORM
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
ms.openlocfilehash: 621a01accf3c323f8098da68667f06f48b9d169b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457247"
---
# <a name="xform-structure"></a>XFORM 结构

`XFORM`结构具有以下形式：

## <a name="syntax"></a>语法

```
typedef struct  tagXFORM {  /* xfrm */
    FLOAT eM11;
    FLOAT eM12;
    FLOAT eM21;
    FLOAT eM22;
    FLOAT eDx;
    FLOAT eDy;
} XFORM;
```

## <a name="remarks"></a>备注

`XFORM`结构指定页面空间转换到世界空间。 `eDx`和`eDy`成员分别指定水平和垂直转换组件。 下表显示了如何使用其他成员，具体取决于该操作：

|操作|eM11|eM12|eM21|eM22|
|---------------|----------|----------|----------|----------|
|`Rotation`|旋转角度的余弦值|旋转角度的正弦值|负旋转角度的正弦值|旋转角度的余弦值|
|`Scaling`|水平缩放的组件|Nothing|Nothing|垂直缩放组件|
|`Shear`|Nothing|水平比例常量|垂直比例常量|Nothing|
|`Reflection`|水平反射组件|Nothing|Nothing|垂直反射组件|

## <a name="requirements"></a>要求

**标头：** wingdi.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

