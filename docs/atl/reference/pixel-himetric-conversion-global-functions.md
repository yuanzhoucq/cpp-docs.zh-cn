---
title: Pixel-HIMETRIC 转换全局函数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326147"
---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 转换全局函数

这些函数支持将像素和 HIMETRIC 单位转换为和转换。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|将 HIMETRIC 单位（每个单位为 0.01 毫米）转换为像素。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|将像素转换为 HIMETRIC 单位（每个单位为 0.01 毫米）。|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>atlhimetricto像素

将以 HIMETRIC 为单位（每个单位是 0.01 毫米）的对象大小转换为以屏幕设备上的像素为单位的大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>参数

*lpsizeinhimetric*<br/>
[在]指针指向以 HIMETRIC 单位为单位的对象大小。

*lpsizeInPix*<br/>
[出]指向要返回对象大小（以像素为单位）的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixeltohimetric

将以屏幕设备上的像素为单位的对象大小转换为以 HIMETRIC 为单位（每个单位是 0.01 毫米）的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>参数

*lpsizeInPix*<br/>
[在]指向对象大小（以像素为单位）的指针。

*lpsizeinhimetric*<br/>
[出]指向要返回对象大小（以 HIMETRIC 单位为单位）的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
