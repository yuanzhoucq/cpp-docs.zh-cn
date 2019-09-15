---
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 155b9f635f6e8c3dc5acb61126f41c49cd32601f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941107"
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
指向**fenv_t**对象的指针，该对象包含通过调用[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)设置的浮点环境。 还可以通过使用**FE_DFL_ENV**宏指定默认启动浮点环境。

## <a name="return-value"></a>返回值

如果已成功设置环境，则返回 0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Fesetenv**函数通过*penv*指向的**fenv_t**对象中存储的值设置当前浮点环境。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 这包括舍入模式和浮点异常的状态标志。  如果*penv*不是**FE_DFL_ENV**或未指向有效的**fenv_t**对象，则不定义后续行为。

对此函数的调用将设置*penv*对象中的异常状态标志，但不会引发这些异常。

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
