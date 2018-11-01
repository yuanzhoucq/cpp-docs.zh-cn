---
title: _get_terminate
ms.date: 11/04/2016
apiname:
- _get_terminate
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
- get_terminate
- _get_terminate
- __get_terminate
helpviewer_keywords:
- __get_terminate function
- get_terminate function
- _get_terminate function
ms.assetid: c8f168c4-0ad5-4832-a522-dd1ef383c208
ms.openlocfilehash: 438bd287738f121efb436857c54c5a68427d9fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484940"
---
# <a name="getterminate"></a>_get_terminate

返回调用的终止例程**终止**。

## <a name="syntax"></a>语法

```C
terminate_function _get_terminate( void );
```

## <a name="return-value"></a>返回值

返回指向 [set_terminate](set-terminate-crt.md) 注册的函数的指针。 如果已设置函数，返回值可能用于还原默认行为;此值可能**NULL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_terminate**|\<eh.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
