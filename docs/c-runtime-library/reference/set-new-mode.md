---
title: _set_new_mode | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _set_new_mode
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
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0fa7022c5195882145452fa14e0cbf7347573a0a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="setnewmode"></a>_set_new_mode

设置新的处理程序模式**malloc**。

## <a name="syntax"></a>语法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>参数

*newhandlermode*<br/>
新的处理程序模式**malloc**; 有效值为 0 或 1。

## <a name="return-value"></a>返回值

返回上一个处理程序模式设置为**malloc**。 返回值为 1，表示，在无法分配内存， **malloc**之前调用新的处理程序例程; 返回值 0 指示它没有。 如果*newhandlermode*参数不等于 0 或 1 时，将返回-1。

## <a name="remarks"></a>备注

C++ **_set_new_mode** 函数将为 [malloc](malloc.md) 设置新的处理程序模式。 新的处理程序模式指示是否在失败时， **malloc**是由设置调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下， **malloc**不调用新处理程序例程上分配内存失败。 你可以重写此默认行为，以便，当**malloc**无法分配内存， **malloc**调用新处理程序例程中相同的方式**新**就是秒当失败时出于同样的原因。 有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 运算符。 若要重写默认值，请调用：

```cpp
_set_new_mode(1);
```

在程序的早期进行调用，或链接到 Newmode.obj（请参阅[链接选项](../../c-runtime-library/link-options.md)）。

此函数验证其参数。 如果*newhandlermode*任何内容而非 0 或 1，该函数时，将调用无效参数处理程序，作为中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则 **_ * * * set_new_mode**返回-1 并设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
