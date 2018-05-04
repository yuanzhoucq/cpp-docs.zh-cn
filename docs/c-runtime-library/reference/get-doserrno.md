---
title: _get_doserrno | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
dev_langs:
- C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7cef2c068fad2f18cb1d11d33e551588800cb64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getdoserrno"></a>_get_doserrno

获取之前它将转换为返回的操作系统的错误值**errno**值。

## <a name="syntax"></a>语法

```C
errno_t _get_doserrno( 
   int * pValue 
);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指向要使用的当前值填充的整数的指针 **_doserrno**全局宏。

## <a name="return-value"></a>返回值

如果 **_get_doserrno**成功，它将返回零; 如果失败，则返回错误代码。 如果*pValue*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Doserrno**全局宏设置为零 CRT 初始化期间，在过程之前执行开始。 将它设置为由返回操作系统错误的任一系统级函数调用返回的操作系统错误值，而且在执行过程中永远不会将其重置为零。 当你编写代码以检查错误值返回的函数，始终清除 **_doserrno**使用[_set_doserrno](set-doserrno.md)函数调用之前。 因为另一个函数调用可能会覆盖 **_doserrno**，通过检查值 **_get_doserrno**紧跟函数调用。

我们建议[_get_errno](get-errno.md)而不是 **_get_doserrno**可移植的错误代码。

可能的值的 **_doserrno**中定义\<.h >。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

**_get_doserrno**是 Microsoft 扩展。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_set_doserrno](set-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
