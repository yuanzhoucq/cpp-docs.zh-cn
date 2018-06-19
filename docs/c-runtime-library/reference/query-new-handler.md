---
title: _query_new_handler | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 340574a57bf1e6309ac9a5e1aa59b7e28632ae59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400994"
---
# <a name="querynewhandler"></a>_query_new_handler

返回当前新处理程序例程的地址。

## <a name="syntax"></a>语法

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>返回值

返回当前新处理程序例程的地址，如所设置 **_set_new_handler**。

## <a name="remarks"></a>备注

C + + **_query_new_handler**函数返回由 c + + 设置的当前异常处理函数的地址[_set_new_handler](set-new-handler.md)函数。 **_set_new_handler**用于指定是如果获取控制权的异常处理函数**新**运算符无法分配内存。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
