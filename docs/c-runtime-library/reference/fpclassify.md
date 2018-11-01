---
title: fpclassify
ms.date: 04/05/2018
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: 626e356cf61415e4f8212a8a12d90a72fe4576bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613871"
---
# <a name="fpclassify"></a>fpclassify

返回参数的浮点分类。

## <a name="syntax"></a>语法

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only

```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**fpclassify**返回一个整数值，该值指示参数的浮点类*x*。 此表显示了可能的值返回**fpclassify**中定义\<math.h >。

|“值”|描述|
|-----------|-----------------|
|**FP_NAN**|静态、信令或不确定的 NaN|
|**FP_INFINITE**|正或负无穷大|
|**FP_NORMAL**|标准化非零正值或负值|
|**FP_SUBNORMAL**|非标准化的正值或负值|
|**FP_ZERO**|零正值或负值|

## <a name="remarks"></a>备注

在 C 中， **fpclassify**是一个宏; 在 c + + **fpclassify**取决于重载使用的参数类型**float**， **double**，或**长** **double**。 在任一情况下，返回的值取决于参数表达式的有效类型，而不是任何中间表示形式。 例如，一个普通**双**或**长** **double**值可以成为无穷大、 非常规，或零值转换为时**float**。

## <a name="requirements"></a>要求

|函数/宏|必需的标头 (C)|必需的标头 (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> 或 \<cmath>|

**Fpclassify**宏和**fpclassify**函数符合 ISO C99 和 C + + 11 规范。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
