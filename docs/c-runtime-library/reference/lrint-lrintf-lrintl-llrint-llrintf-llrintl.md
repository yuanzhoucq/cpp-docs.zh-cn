---
title: lrint、lrintf、lrintl、llrint、llrintf、llrintl
ms.date: 04/05/2018
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: c7831842eb4d3c1eef9c4c9e83bbddb557cec0e3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857744"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint、lrintf、lrintl、llrint、llrintf、llrintl

使用当前舍入模式和方向将指定浮点值舍入到最接近的整数值。

## <a name="syntax"></a>语法

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
要舍入的值。

## <a name="return-value"></a>返回值

如果成功，则返回*x*的舍入整数值。

|问题|返回|
|-----------|------------|
|*x*超出了返回类型的范围<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|引发**FE_INVALID**并返回零（0）。|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**lrint**和**llrint**的重载，该重载采用**float**和**long** **double**类型。 在 C 程序中， **lrint**和**llrint**始终采用**double**。

如果*x*不表示整数值的浮点等效项，则这些函数将引发**FE_INEXACT**。

**Microsoft 专用**：当结果在返回类型范围之外时，或者参数为 NaN 或无穷大时，返回值为 "已定义实现"。 Microsoft 编译器返回零 (0) 值。

## <a name="requirements"></a>需求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**lrint**、 **lrintf**、 **lrintl**、 **llrint**、 **llrintf**、 **llrintl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参见 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
