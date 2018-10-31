---
title: PIXEL-HIMETRIC 转换全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 659bc5a1aea1a6e16a3cccbdf63684212a88f2f9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061256"
---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 转换全局函数

这些函数为从像素和 HIMETRIC 为单位进行来回转换提供支持。

> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|将 HIMETRIC 为单位 （每个单位是 0.01 毫米） 转换为像素。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|将像素转换为 HIMETRIC 为单位 （每个单位是 0.01 毫米）。|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

将以 HIMETRIC 为单位（每个单位是 0.01 毫米）的对象大小转换为以屏幕设备上的像素为单位的大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>参数

*lpSizeInHiMetric*<br/>
[in]指向以 HIMETRIC 为单位的对象的大小。

*lpSizeInPix*<br/>
[out]指向对象的大小 （像素） 将返回的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

将以屏幕设备上的像素为单位的对象大小转换为以 HIMETRIC 为单位（每个单位是 0.01 毫米）的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>参数

*lpSizeInPix*<br/>
[in]指向对象的大小 （像素）。

*lpSizeInHiMetric*<br/>
[out]指向其中以 HIMETRIC 为单位的对象的大小是要返回的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>要求

**标头：** atlwin.h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
