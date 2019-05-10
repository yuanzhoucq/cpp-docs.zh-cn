---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334380"
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
指向**fenv_t**对象，以包含浮点环境的副本。

## <a name="return-value"></a>返回值

当且仅当该函数是能够成功启用不间断的浮点异常处理，则返回零。

## <a name="remarks"></a>备注

**Feholdexcept**函数用于存储中的当前浮动点环境状态**fenv_t**指向对象*penv*，并将环境设置为不会中断浮点异常执行。 这被称为不间断模式。  此模式将继续，直到使用 [fesetenv](fesetenv1.md) 或 [feupdateenv](feupdateenv.md) 恢复环境。

在需要隐藏来自调用方的一个或多个浮点异常的子例程的开头，可以使用此函数。 若要报告异常，您可以只需清除不需要的异常通过[feclearexcept](feclearexcept1.md) ，然后结束通过调用不间断模式**feupdateenv**。

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
