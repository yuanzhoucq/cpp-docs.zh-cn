---
title: isnan、_isnan、_isnanf | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isnan
- _isnanf
- isnan
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs:
- C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baf92397087ebbac27c7fea8cf5f524b33736b19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401147"
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf

测试浮点值是否不是一个数字 (NAN)。

## <a name="syntax"></a>语法

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

在 C 中， **isnan**宏和 **_isnan**和 **_isnanf**函数返回一个非零值，如果自变量*x*是 NAN; 否则为它们返回 0。

C + + 中**isnan**模板函数将返回**true**如果自变量*x*是 NAN; 否则它们会返回**false**。

## <a name="remarks"></a>备注

C **isnan**宏和 **_isnan**和 **_isnanf**函数测试浮点值*x*，返回一个非零值，如果*x*不是一个数字 (NAN) 值。 如果无法为指定类型以 IEEE 754 浮点格式表示浮点运算的结果，则会生成 NAN。 有关如何将 NAN 表示为输出的信息，请参阅 [printf](printf-printf-l-wprintf-wprintf-l.md)。

当编译为 c + +， **isnan**未定义宏，和**isnan**改为定义模板函数。 它将返回类型的值**bool**而不是整数。

**_Isnan**和 **_isnanf**函数是 Microsoft 特定。 **_Isnanf**函数仅在针对 x64 编译时可用。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**， **_isnanf**|\<math.h>|\<math.h> 或 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 或 \<cfloat>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_finite、_finitef](finite-finitef.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
