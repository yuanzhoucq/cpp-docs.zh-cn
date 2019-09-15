---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941248"
---
# <a name="fegetenv"></a>fegetenv

在指定对象中存储当前浮点环境。

## <a name="syntax"></a>语法

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>参数

*penv*<br/>
指向包含当前浮点环境值的**fenv_t**对象的指针。

## <a name="return-value"></a>返回值

如果已成功将浮点环境存储在*penv*中，则返回0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Fegetenv**函数在*penv*指向的对象中存储当前浮点环境。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 包括舍入方向模式和浮点异常的状态标志。  如果*penv*未指向有效的**fenv_t**对象，则不定义后续行为。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
