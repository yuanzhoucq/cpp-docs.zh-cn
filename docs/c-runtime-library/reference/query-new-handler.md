---
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 9c87a63a9ed94eb1473230aedb5e9c17fcc6410b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216838"
---
# <a name="_query_new_handler"></a>_query_new_handler

返回当前新处理程序例程的地址。

## <a name="syntax"></a>语法

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>返回值

返回 **_set_new_handler**设置的当前新处理程序例程的地址。

## <a name="remarks"></a>备注

C + + **_query_new_handler**函数返回 c + + [_set_new_handler](set-new-handler.md)函数设置的当前异常处理函数的地址。 **_set_new_handler**用于指定一个异常处理函数，该函数将在 **`new`** 运算符无法分配内存时获得控制权。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[忙](free.md)<br/>
