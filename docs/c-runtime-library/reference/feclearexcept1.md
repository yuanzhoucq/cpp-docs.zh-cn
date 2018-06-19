---
title: feclearexcept1 | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- feclearexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feclearexcept
- fenv/feclearexcept
dev_langs:
- C++
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe943bcc0a1e1a027e432911bd2ad722fc7c7c1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399018"
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

返回零如果*excepts*为零，或如果已成功清除所有指定的异常。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Feclearexcept**函数尝试清除浮点点指定的异常状态标志*excepts*。 此函数支持在 fenv.h 中定义的这些异常宏：

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|

*Excepts*参数可能为零或一个或多个受支持的异常宏的按位或。 任何其他参数值的结果均未定义。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
