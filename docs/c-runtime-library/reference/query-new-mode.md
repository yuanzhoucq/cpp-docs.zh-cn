---
title: _query_new_mode
ms.date: 11/04/2016
apiname:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 327f22c847793316bd126721b4a66846d7da84dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620020"
---
# <a name="querynewmode"></a>_query_new_mode

返回一个整数，指示由设置的新处理程序模式 **_set_new_mode**有关**malloc**。

## <a name="syntax"></a>语法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>返回值

返回当前新处理程序模式，即 0 或 1， **malloc**。 返回值为 1 表示，在分配内存失败**malloc**调用新处理程序例程; 返回值 0 表示它将不做。

## <a name="remarks"></a>备注

C + + **_query_new_mode**函数将返回一个整数，指示由 c + + 设置的新处理程序模式[_set_new_mode](set-new-mode.md)函数[malloc](malloc.md)。 新的处理程序模式将指示是否在失败来分配内存， **malloc**是所设置的调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下**malloc**不会在失败时调用新处理程序例程。 可以使用 **_set_new_mode**重写此行为，因此在失败**malloc**调用新处理程序例程中相同的方式**新**运算符执行到失败时分配的内存。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
