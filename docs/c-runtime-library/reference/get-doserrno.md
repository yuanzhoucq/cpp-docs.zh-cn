---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 7b889bccc0b1f1fd99a9a0526bbfb42a2e520970
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919386"
---
# <a name="_get_doserrno"></a>_get_doserrno

获取由操作系统返回的错误值，在将其转换为**errno**值之前。

## <a name="syntax"></a>语法

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指向要使用 **_doserrno**全局宏的当前值填充的整数的指针。

## <a name="return-value"></a>返回值

如果 **_get_doserrno**成功，则返回零;如果失败，则返回错误代码。 如果*pValue*为**NULL**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

在开始执行进程之前，在 CRT 初始化过程中 **_doserrno**全局宏设置为零。 将它设置为由返回操作系统错误的任一系统级函数调用返回的操作系统错误值，而且在执行过程中永远不会将其重置为零。 当你编写代码来检查函数返回的错误值时，请始终通过在函数调用之前使用[_set_doserrno](set-doserrno.md)来清除 **_doserrno** 。 由于另一个函数调用可能会覆盖 **_doserrno**，因此请在函数调用之后立即使用 **_get_doserrno**检查值。

对于可移植错误代码，我们建议[_get_errno](get-errno.md)而不是 **_get_doserrno** 。

**_Doserrno**的可能值在 errno> \<中定义。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

**_get_doserrno**是 Microsoft 扩展。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[_set_doserrno](set-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
