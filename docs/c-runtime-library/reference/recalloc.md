---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338125"
---
# <a name="_recalloc"></a>_recalloc

**真实和****卡洛克**的组合。 重新分配内存中的数组并将其元素初始化为 0。

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

*number*<br/>
元素数量。

*大小*<br/>
每个元素的长度（以字节为单位）。

## <a name="return-value"></a>返回值

**_recalloc**返回指向重新分配（并可能移动）内存块**的空**指针。

如果没有足够的可用内存将块扩展到给定的大小，则原始块保持不变，并且**返回 NULL。**

如果请求的大小为零，则释放*memblock*指向的块;如果请求的大小为零。"返回值为**NULL***NULL，memblock*被保留在已释放的块上。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 要获取指向**void**以外的类型的指针，请使用返回值上强制转换的类型。

## <a name="remarks"></a>备注

**_recalloc**函数更改已分配内存块的大小。 *memblock*参数指向内存块的开头。 如果*memblock*为**NULL，****则_recalloc**与[calloc](calloc.md)相同的方式，并分配一个新的*编号* * *大小*字节块。 将每个元素初始化为 0。 如果*memblock*不是**NULL，** 它应该是前一个调用 call 返回的指向**calloc、malloc**或[realloc](malloc.md)的指针。 [realloc](realloc.md)

由于新块可以位于新的内存位置，因此 **_recalloc**返回的指针不能保证是通过*memblock*参数传递的指针。

**_recalloc**如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ，** 则将**errno**设置到**ENOMEM。** 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**调用**realloc**以使用[C++_set_new_mode](set-new-mode.md)函数来设置新的处理程序模式。 新的处理程序模式指示**realloc**在发生故障时是否调用[由 _set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下 **，Realloc**不会在分配内存失败时调用新的处理程序例程。 您可以重写此默认行为，以便在 **_recalloc**无法分配内存时 **，Realloc**调用新处理程序例程的方式**与新运算符出于**相同原因失败时相同。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ。

当应用程序链接到 C 运行时库的调试版本时 **，_recalloc**解析为[_recalloc_dbg](recalloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**标记为`__declspec(noalias)`，`__declspec(restrict)`表示保证函数不修改全局变量，并且返回的指针不会别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[自由](free.md)<br/>
[链接选项](../../c-runtime-library/link-options.md)<br/>
