---
title: _swab
ms.date: 11/04/2016
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 64753383bcb94947e6b413b5f55ac6e2d9c7dbca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603029"
---
# <a name="swab"></a>_swab

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

*dest*<br/>
已交换数据的存储位置。

*n*<br/>
要复制和交换的字节数。

## <a name="return-value"></a>返回值

**Swab**函数不返回值。 该函数设置**errno**到**EINVAL**如果*src*或者*dest*指针为 null 或*n*小于零，并且无效的参数处理程序调用，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

有关此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

如果*n*为偶数， **_swab**函数副本*n*个字节从*src*，交换每对相邻的字节，并将存储在结果*dest*。 如果*n*为奇数， **_swab**复制并交换第一个*n*-1 个字节的*src*，并不复制最后一个字节。 **_Swab**函数通常用于准备传输到使用不同的字节顺序的计算机的二进制数据。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_swab**|C：\<stdlib.h> C++：\<cstdlib> 或 \<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
