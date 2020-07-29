---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 26fabc71337f1554b63909697b601a0bd9e86638
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216825"
---
# <a name="_query_new_mode"></a>_query_new_mode

返回一个整数，该整数指示为**malloc** **_set_new_mode**设置的新处理程序模式。

## <a name="syntax"></a>语法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>返回值

对于**malloc**，返回当前新处理程序模式，即0或1。 返回值1表示在分配内存失败时， **malloc**调用新的处理程序例程;返回值为0指示它不会。

## <a name="remarks"></a>备注

C + + **_query_new_mode**函数返回一个整数，该整数指示为由[Malloc](malloc.md)的 c + + [_set_new_mode](set-new-mode.md)函数设置的新处理程序模式。 新处理程序模式指示在分配内存失败时， **malloc**是否调用由[_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下， **malloc**不会在失败时调用新的处理程序例程。 你可以使用 **_set_new_mode**重写此行为，以便在失败**malloc**调用新的处理程序例程，方法与该 **`new`** 运算符在无法分配内存时所执行的操作相同。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[忙](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
