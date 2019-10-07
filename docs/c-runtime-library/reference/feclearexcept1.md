---
title: feclearexcept1
ms.date: 04/05/2018
api_name:
- feclearexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 9899d7068a289e7d5f71cb42a8373869d60c3070
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941275"
---
# <a name="feclearexcept"></a>feclearexcept

尝试清除由参数指定的浮点异常标记。

## <a name="syntax"></a>语法

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>参数

*excepts*<br/>
要清除的异常状态标记。

## <a name="return-value"></a>返回值

如果*removed*为零，则返回零; 如果已成功清除所有指定的异常，则返回零。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Feclearexcept**函数尝试清除*removed*指定的浮点异常状态标志。 此函数支持在 fenv.h 中定义的这些异常宏：

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALL_EXCEPT|所有受支持的浮点异常的按位 OR。|

*Removed*参数可以是零，也可以是一个或多个受支持的异常宏的按位 or。 任何其他参数值的结果均未定义。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
