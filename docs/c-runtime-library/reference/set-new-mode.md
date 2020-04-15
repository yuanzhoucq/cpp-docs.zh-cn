---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332324"
---
# <a name="_set_new_mode"></a>_set_new_mode

设置**Malloc**的新处理程序模式。

## <a name="syntax"></a>语法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>参数

*新处理程序模式*<br/>
**MALLoc**的新处理程序模式 ;有效值为 0 或 1。

## <a name="return-value"></a>返回值

返回为**malloc**设置的上一个处理程序模式。 返回值 1 表示，在分配内存失败时，malloc 以前调用了新的处理程序例程;否则 **，malloc**调用了新的处理程序例程。返回值 0 表示没有。 如果*newhandlermode*参数不等于 0 或 1，则返回 -1。

## <a name="remarks"></a>备注

C++ **_set_new_mode** 函数将为 [malloc](malloc.md) 设置新的处理程序模式。 新的处理程序模式指示在发生故障时 **，malloc**是否将调用[由 _set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下 **，malloc**不会在分配内存失败时调用新的处理程序例程。 您可以重写此默认行为，以便在**malloc**无法分配内存时 **，malloc**调用新处理程序例程的方式**与新运算符出于**相同原因失败时相同的方式调用新处理程序例程。 有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 运算符。 若要重写默认值，请调用：

```cpp
_set_new_mode(1);
```

在程序的早期进行调用，或链接到 Newmode.obj（请参阅[链接选项](../../c-runtime-library/link-options.md)）。

此函数验证其参数。 如果*newhandlermode*是除 0 或 1 以外的任何内容，则函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行<strong>，_set_new_mode</strong>返回 -1 并将**errno** `EINVAL`设置到 。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
