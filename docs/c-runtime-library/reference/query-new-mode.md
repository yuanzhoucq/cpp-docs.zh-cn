---
title: _query_new_mode | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8907b043e8b4441d6e5213a1d386dbc1a5a6910a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405713"
---
# <a name="querynewmode"></a>_query_new_mode

返回一个整数，指示在新的处理程序模式，设置 **_set_new_mode**为**malloc**。

## <a name="syntax"></a>语法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>返回值

返回当前新处理程序的模式，即 0 或 1， **malloc**。 返回值为 1，表示，在无法分配内存， **malloc**调用新的处理程序例程; 返回值 0 表示它将不做。

## <a name="remarks"></a>备注

C + + **_query_new_mode**函数返回一个整数，指示由 c + + 设置新处理程序模式[_set_new_mode](set-new-mode.md)函数[malloc](malloc.md)。 新的处理程序模式指示是否在无法分配内存， **malloc**是由设置调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下， **malloc**不调用新处理程序例程失败。 可以使用 **_set_new_mode**因此重写此行为，失败**malloc**调用新处理程序例程中相同的方式**新**到失败时，会执行运算符分配内存。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
