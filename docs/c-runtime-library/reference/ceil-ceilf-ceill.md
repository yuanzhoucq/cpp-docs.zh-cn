---
title: ceil、ceilf、ceill | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
apilocation:
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68ff857db09d1426fbed6ea497624e13cc362a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394260"
---
# <a name="ceil-ceilf-ceill"></a>ceil、ceilf、ceill

计算一个值的上限。

## <a name="syntax"></a>语法

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

## <a name="return-value"></a>返回值

**Ceil**函数将返回表示大于或等于最小整数的浮点值*x*。 无错误返回。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|无|**_DOMAIN**|

**ceil**具有使用流式处理 SIMD 扩展 2 (SSE2) 实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**ceil**采用**float**或**长** **double**类型。 在 C 程序中， **ceil**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**ceil**， **ceilf**， **ceill**|\<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [floor](floor-floorf-floorl.md) 的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
