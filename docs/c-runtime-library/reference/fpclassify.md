---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957068"
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

**fpclassify**返回一个整数值，该值指示参数*x*的浮点类。 此表显示**fpclassify**中\<定义的可能值，>。

|值|描述|
|-----------|-----------------|
|**FP_NAN**|静态、信令或不确定的 NaN|
|**FP_INFINITE**|正或负无穷大|
|**FP_NORMAL**|标准化非零正值或负值|
|**FP_SUBNORMAL**|非标准化的正值或负值|
|**FP_ZERO**|零正值或负值|

## <a name="remarks"></a>备注

在 C 中， **fpclassify**是一个宏;在C++中， **fpclassify**是使用**float**、 **double**或**long** **double**参数类型重载的函数。 在任一情况下，返回的值取决于参数表达式的有效类型，而不是任何中间表示形式。 例如，在转换为**浮点**值时，正常的**double**或**long** **double**值可以变成无限大、denormal 或零值。

## <a name="requirements"></a>要求

|函数/宏|必需的标头 (C)|必需的标头 (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> 或 \<cmath>|

**Fpclassify**宏和**FPCLASSIFY**函数符合 ISO C99 和 c + + 11 规范。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
