---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362183"
---
# <a name="_umask_s"></a>_umask_s

设置默认的文件权限掩码。 这是 [_umask](umask.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。

## <a name="syntax"></a>语法

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>参数

*模式*<br/>
默认权限设置。

*pOldMode*<br/>
权限设置的上一个值。

## <a name="return-value"></a>返回值

如果*模式*未指定有效模式或*pOldMode*指针为**NULL，** 则返回错误代码。

### <a name="error-conditions"></a>错误条件

|*模式*|*pOldMode*|返回值|*pOldMode*的内容|
|------------|----------------|----------------------|--------------------------------|
|any|**空**|**埃因瓦尔**|未修改|
|无效模式|any|**埃因瓦尔**|未修改|

发生上述情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，_umask_s**返回**EINVAL**并将**errno**设置到**EINVAL**。

## <a name="remarks"></a>备注

**_umask_s**函数将当前进程的文件权限掩码设置为*模式*指定的模式。 文件权限掩码修改由 **_creat、_open**或 **_sopen**创建的新文件的权限 **_open**设置。 如果掩码中的一位是 1，则将文件的请求权限值中相应的一位设置为 0 (不允许)。 如果掩码中的一位是 0，则相应的一位保留不变。 直至首次关闭新文件时才会设置新文件的权限设置。

整数表达式*pmode*包含以下一个或两个清单常量，在 SYS_STAT 中定义。H：

|*pmode*||
|-|-|
|**_S_IWRITE**|允许写入。|
|**_S_IREAD**|允许读取。|
|**_S_IREAD_S_IWRITE** \| **_S_IWRITE**|允许读取和写入。|

当两个常量都给出时，它们与位-OR 运算符 （）**|** 联接。 如果*模式*参数**为_S_IREAD，** 则不允许读取（该文件仅写入）。 如果*模式*参数**是_S_IWRITE，** 则不允许写入（该文件是只读的）。 例如，如果掩码中设置了写入位，则任何新文件都将为只读。 请注意在 MS-DOS 和 Windows 操作系统下，所有文件均可读；不可能提供只写权限。 因此，使用 **_umask_s**设置读取位对文件模式没有影响。

如果*pmode*不是清单常量之一的组合，或者合并了一组备用常量，则函数将忽略这些常量。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_umask_s**|\<io.h> 和 \<sys/stat.h> 和 \<sys/types.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[低电平 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
