---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941190"
---
# <a name="feholdexcept"></a>feholdexcept

将当前浮点环境保存在指定对象中，清除浮点状态标志，如果可能，请将浮点环境置于不间断模式。

## <a name="syntax"></a>语法

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>参数

*penv*<br/>
指向**fenv_t**对象的指针，该对象包含浮点环境的副本。

## <a name="return-value"></a>返回值

当且仅当函数能够成功启用非停止浮点异常处理时，返回零。

## <a name="remarks"></a>备注

**Feholdexcept**函数用于将当前浮点环境的状态存储在*penv*指向的**fenv_t**对象中，并将环境设置为不会中断对浮点异常的执行。 这被称为不间断模式。  此模式将继续，直到使用 [fesetenv](fesetenv1.md) 或 [feupdateenv](feupdateenv.md) 恢复环境。

在需要隐藏来自调用方的一个或多个浮点异常的子例程的开头，可以使用此函数。 若要报告异常，只需通过使用 feclearexcept 清除不需要的异常[，](feclearexcept1.md)并通过调用**feupdateenv**结束非停止模式。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
