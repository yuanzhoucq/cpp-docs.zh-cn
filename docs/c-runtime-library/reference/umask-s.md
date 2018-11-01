---
title: _umask_s
ms.date: 11/04/2016
apiname:
- _umask_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 878a22cb2884c36e792ff8dead1453582addb5b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480661"
---
# <a name="umasks"></a>_umask_s

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

如果返回错误代码*模式下*未指定有效的模式或*pOldMode*指针位于**NULL**。

### <a name="error-conditions"></a>错误条件

|*模式*|*pOldMode*|返回值|内容*pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|任何|**NULL**|**EINVAL**|未修改|
|无效模式|任何|**EINVAL**|未修改|

发生上述情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则 **_umask_s**返回**EINVAL**并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**_Umask_s**函数将当前进程的文件权限掩码设置为所指定的模式*模式*。 文件权限掩码修改创建的新文件的权限设置 **_creat**， **_open**，或 **_sopen**。 如果掩码中的一位是 1，则将文件的请求权限值中相应的一位设置为 0 (不允许)。 如果掩码中的一位是 0，则相应的一位保留不变。 直至首次关闭新文件时才会设置新文件的权限设置。

整数表达式*pmode*包含一个或两个 SYS\STAT 中定义的以下清单常量。H:

|*pmode*||
|-|-|
|**_S_IWRITE**|允许写入。|
|**_S_IREAD**|允许读取。|
|**_S_IREAD** \| **_S_IWRITE**|允许读取和写入。|

当给定这两个常量时，它们使用按位 OR 运算符联接 ( **|** )。 如果*模式下*自变量是 **_S_IREAD**，则不允许读取 （此文件为只写）。 如果*模式下*自变量是 **_S_IWRITE**，则不允许写入 （文件是只读的）。 例如，如果掩码中设置了写入位，则任何新文件都将为只读。 请注意在 MS-DOS 和 Windows 操作系统下，所有文件均可读；不可能提供只写权限。 因此，设置读取位与 **_umask_s**不起作用的文件模式。

如果*pmode*不是清单常量之一的组合或合并了一组替代常量，该函数将会忽略这些。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_umask_s**|\<io.h> 和 \<sys/stat.h> 和 \<sys/types.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
