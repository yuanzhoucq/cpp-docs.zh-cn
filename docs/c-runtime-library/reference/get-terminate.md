---
title: _get_terminate
ms.date: 4/2/2020
api_name:
- _get_terminate
- _o__get_terminate
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
- get_terminate
- _get_terminate
- __get_terminate
helpviewer_keywords:
- __get_terminate function
- get_terminate function
- _get_terminate function
ms.assetid: c8f168c4-0ad5-4832-a522-dd1ef383c208
ms.openlocfilehash: fff90037851b23f3525f514aba0f6f913f9dd776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344924"
---
# <a name="_get_terminate"></a>_get_terminate

返回要由**终止**调用的终止例程。

## <a name="syntax"></a>语法

```C
terminate_function _get_terminate( void );
```

## <a name="return-value"></a>返回值

返回指向 [set_terminate](set-terminate-crt.md) 注册的函数的指针。 如果未设置任何函数，则返回值可用于还原默认行为;如果未设置任何函数，则返回值可用于还原默认行为。此值可以是**NULL**。

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_terminate**|\<eh.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[中止](abort.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[终止](terminate-crt.md)<br/>
[意外](unexpected-crt.md)<br/>
