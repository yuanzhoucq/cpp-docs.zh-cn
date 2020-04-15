---
title: _aligned_malloc
ms.date: 4/2/2020
api_name:
- _aligned_malloc
- _o__aligned_malloc
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
- _aligned_malloc
- alligned_malloc
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
ms.openlocfilehash: b7d7f29f50b28ff713de94cc3304014e96d45b70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350605"
---
# <a name="_aligned_malloc"></a>_aligned_malloc

在指定对齐边界分配内存。

## <a name="syntax"></a>语法

```C
void * _aligned_malloc(
    size_t size,
    size_t alignment
);
```

### <a name="parameters"></a>参数

*大小*<br/>
请求的内存分配的大小。

*对齐 (alignment)*<br/>
对齐值，必须是 2 的整数次幂。

## <a name="return-value"></a>返回值

如果操作失败，指向已分配的内存块的指针或 NULL。 指针是对齐的倍*数*。

## <a name="remarks"></a>备注

**_aligned_malloc**是基于[马洛克](malloc.md)。

**_aligned_malloc**标记为`__declspec(noalias)`，`__declspec(restrict)`表示保证函数不修改全局变量，并且返回的指针不会别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

如果内存分配失败或请求的大小大于 `errno`，则此函数会将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外 **，_aligned_malloc**验证其参数。 如果*对齐*不是 2 的功率或*大小*为零，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 NULL`errno`并`EINVAL`设置到 。

使用[_aligned_free](aligned-free.md)来解分配 **_aligned_malloc**和`_aligned_offset_malloc`获得的内存。 不要使用`free`，这不能正确回收对齐的内存，并可能导致难以诊断的错误。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_malloc**|\<malloc.h>|

## <a name="example"></a>示例

```C
// crt_aligned_malloc.c

#include <malloc.h>
#include <stdio.h>

int main() {
    void    *ptr;
    size_t  alignment,
            off_set;

    // Note alignment should be 2^N where N is any positive int.
    alignment = 16;
    off_set = 5;

    // Using _aligned_malloc
    ptr = _aligned_malloc(100, alignment);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned memory.");
        return -1;
    }
    if (((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);

    // Using _aligned_realloc
    ptr = _aligned_realloc(ptr, 200, alignment);
    if ( ((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);
    _aligned_free(ptr);

    // Using _aligned_offset_malloc
    ptr = _aligned_offset_malloc(200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu "
                  "and alignment %zu\n",ptr, off_set, alignment);

    // Using _aligned_offset_realloc
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error reallocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu and "
                  "alignment %zu\n", ptr, off_set, alignment);

    // Note that _aligned_free works for both _aligned_malloc
    // and _aligned_offset_malloc. Using free is illegal.
    _aligned_free(ptr);
}
```

```Output
This pointer, 3280880, is aligned on 16
This pointer, 3280880, is aligned on 16
This pointer, 3280891, is offset by 5 on alignment of 16
This pointer, 3280891, is offset by 5 on alignment of 16
```

## <a name="see-also"></a>另请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)
