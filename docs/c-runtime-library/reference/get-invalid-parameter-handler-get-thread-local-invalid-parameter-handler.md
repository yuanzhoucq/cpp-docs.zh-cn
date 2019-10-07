---
title: _get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 534590fed77fe06149db892d98ba0e555297ac7c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955831"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler

获取在 CRT 检测到无效参数时要调用的函数。

## <a name="syntax"></a>语法

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>返回值

指向当前设置的无效参数处理程序函数的指针，或者如果未设置任何函数，则为空指针。

## <a name="remarks"></a>备注

**_Get_invalid_parameter_handler**函数获取当前设置的全局无效参数处理程序。 如果未设置全局无效参数处理程序，则返回空指针。 同样， **_get_thread_local_invalid_parameter_handler**将获取调用它的线程的当前线程本地无效参数处理程序，如果未设置任何处理程序，则返回空指针。 有关如何设置全局和线程本地无效参数处理程序的信息，请参阅 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。

返回的无效参数处理程序函数指针具有以下类型：

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

有关无效参数处理程序的详细信息，请参阅 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 中的原型。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_invalid_parameter_handler**、 **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> 或 \<stdlib.h>|

**_Get_invalid_parameter_handler**和 **_Get_thread_local_invalid_parameter_handler**函数是 Microsoft 特定的。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[CRT 函数的安全增强版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
