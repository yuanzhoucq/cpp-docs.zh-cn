---
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: f7fe23cd9c1b2eab52ebe50904d0bb18fe16cea6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362953"
---
# <a name="_swab"></a>_swab

交换字节。

## <a name="syntax"></a>语法

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>参数

*src*<br/>
要复制和交换的数据。

dest**<br/>
已交换数据的存储位置。

*n*<br/>
要复制和交换的字节数。

## <a name="return-value"></a>返回值

**拭子**函数不返回值。 如果*src*或*dest*指针为空或*n*小于零，并且调用无效的参数处理程序，则函数将**errno**设置**到 EINVAL，** 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关此代码和其他退货代码的详细信息[，请参阅_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

如果*n*为偶数 **，_swab**函数将*n*字节从*src*复制，交换每对相邻的字节，并将结果存储在*dest*。 如果*n*是奇数 **，_swab**复制并交换*src**的前*n -1 字节，并且不会复制最终字节。 **_swab**函数通常用于准备二进制数据以传输到使用不同的字节顺序的计算机。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_swab**|C：\<stdlib.h> C++：\<cstdlib> 或 \<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>另请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
