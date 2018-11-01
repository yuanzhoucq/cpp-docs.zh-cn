---
title: fesetenv
ms.date: 04/05/2018
apiname:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 8c91bfbb89df964fed0a632d5fb5ebac47ebe948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436129"
---
# <a name="fesetenv"></a>fesetenv

设置当前的浮点环境。

## <a name="syntax"></a>语法

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>参数

*penv*<br/>
指向**fenv_t**对象，其中包含作为组的浮点环境，通过调用[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)。 此外可以通过使用指定的默认启动浮点环境**FE_DFL_ENV**宏。

## <a name="return-value"></a>返回值

如果已成功设置环境，则返回 0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Fesetenv**函数设置当前浮点环境中存储的值从**fenv_t**指向对象*penv*。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 这包括舍入模式和浮点异常的状态标志。  如果*penv*不是**FE_DFL_ENV**或不指向有效**fenv_t**对象，则未定义后续行为。

对此函数的调用设置的异常中的状态标志*penv*对象，但它不会引发这些异常。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
