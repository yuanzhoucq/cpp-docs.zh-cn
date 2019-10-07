---
title: _set_new_mode
ms.date: 11/04/2016
api_name:
- _set_new_mode
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
ms.openlocfilehash: b248f1c97b1ec334b7441f33862b90473e08993f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948446"
---
# <a name="_set_new_mode"></a>_set_new_mode

为**malloc**设置新的处理程序模式。

## <a name="syntax"></a>语法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>参数

*newhandlermode*<br/>
**Malloc**的新处理程序模式;有效值为0或1。

## <a name="return-value"></a>返回值

返回为**malloc**设置的前一个处理程序模式。 返回值1表示在分配内存失败时， **malloc**之前称为新的处理程序例程;如果返回值为0，则表示它不是。 如果*newhandlermode*参数不等于0或1，则返回-1。

## <a name="remarks"></a>备注

C++ **_set_new_mode** 函数将为 [malloc](malloc.md) 设置新的处理程序模式。 新处理程序模式指示在失败时， **malloc**是否调用由[_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下，在无法分配内存时， **malloc**不会调用新的处理程序例程。 您可以重写此默认行为，以便在**malloc**无法分配内存时， **malloc**会调用新的处理程序例程，其方式与在同一原因下**新**运算符失败时相同。 有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 运算符。 若要重写默认值，请调用：

```cpp
_set_new_mode(1);
```

在程序的早期进行调用，或链接到 Newmode.obj（请参阅[链接选项](../../c-runtime-library/link-options.md)）。

此函数验证其参数。 如果*newhandlermode*不是0或1，则函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则<strong>_set_new_mode</strong>将返回-1，并将**errno**设置为`EINVAL`。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
