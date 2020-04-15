---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: efcac6a64c01bee38a3753bdec378dae625db35e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345026"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

获取 **_pgmptr**全局变量的当前值。

## <a name="syntax"></a>语法

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指向要填充 **_pgmptr**变量的当前值的字符串的指针。

## <a name="return-value"></a>返回值

如果成功，则返回零；如果失败，则返回错误代码。 如果*pValue*为**NULL，** 则无效参数处理程序将调用[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数将**errno**设置到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

仅当程序的入口点（如**main（）** 或**WinMain（）））** 时，才呼叫 **_get_pgmptr。** **_pgmptr**全局变量包含与进程关联的可执行文件的完整路径。 有关详细信息，请参阅 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[_get_wpgmptr](get-wpgmptr.md)<br/>
