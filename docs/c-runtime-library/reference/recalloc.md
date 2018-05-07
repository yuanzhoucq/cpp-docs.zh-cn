---
title: _recalloc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _recalloc
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
- _recalloc
- recalloc
dev_langs:
- C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c4ae06fbd3d10f1014fe1c879b482f30302a4f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="recalloc"></a>_recalloc

组合**realloc**和**calloc**。 重新分配内存中的数组并将其元素初始化为 0。

## <a name="syntax"></a>语法

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向之前已分配内存块的指针。

*数*<br/>
元素数量。

*size*<br/>
每个元素的长度（以字节为单位）。

## <a name="return-value"></a>返回值

**_recalloc**返回**void**重新分配的 （并且可能已移动的） 内存块指针。

如果不是内存不足以将块展开到给定的大小，原始块保留不变，和**NULL**返回。

如果请求的大小为零，则指向块*memblock*释放; 返回值是**NULL**，和*memblock*仍指向已释放的块。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而**void**，使用类型强制转换返回值上。

## <a name="remarks"></a>备注

**_Recalloc**函数更改分配的内存块的大小。 *Memblock*参数指向的内存块的开头。 如果*memblock*是**NULL**， **_recalloc**行为与相同的方式[calloc](calloc.md)和分配新块*数* * *大小*字节。 将每个元素初始化为 0。 如果*memblock*不**NULL**，它应返回上次调用的指针**calloc**， [malloc](malloc.md)，或[realloc](realloc.md).

因为新的块可能在新的内存位置，指针返回 **_recalloc**不保证可传递的指针*memblock*自变量。

**_recalloc**设置**errno**到**ENOMEM**如果内存分配失败或内存量请求超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**调用**realloc**才能使用 c + + [_set_new_mode](set-new-mode.md)函数可设置新的处理程序模式。 新的处理程序模式指示是否在失败时， **realloc**是由设置调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下， **realloc**不调用新处理程序例程上分配内存失败。 你可以重写此默认行为，以便，当 **_recalloc**无法分配内存， **realloc**调用新处理程序例程中相同的方式**新**运算符出于相同原因时，会。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ。

当与 C 运行时库的调试版本链接应用程序 **_recalloc**解析为[_recalloc_dbg](recalloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**标记`__declspec(noalias)`和`__declspec(restrict)`，这意味着保证函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[链接选项](../../c-runtime-library/link-options.md)<br/>
