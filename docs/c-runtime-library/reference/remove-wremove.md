---
title: remove、_wremove
ms.date: 11/04/2016
apiname:
- _wremove
- remove
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
- remove
- _wremove
- _tremove
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
ms.openlocfilehash: d5636912ea36fd1b1412a556d516ac3e8184e0b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613962"
---
# <a name="remove-wremove"></a>remove、_wremove

删除文件。

## <a name="syntax"></a>语法

```C
int remove(
   const char *path
);
int _wremove(
   const wchar_t *path
);
```

### <a name="parameters"></a>参数

*path*<br/>
要移除的文件的路径。

## <a name="return-value"></a>返回值

如果成功删除文件，则这些函数将返回 0。 否则，它将返回-1，并设置**errno**到**EACCES**以指示路径指定只读文件或文件已打开，或设置为**ENOENT**指示未找到文件名或路径或者路径指定一个目录。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**remove** 函数删除由  *路径指定的文件。* **_wremove**是宽字符版本**删除 （_r)**;*路径*参数 **_wremove**是宽字符字符串。 **_wremove**并**删除 （_r)** 行为相同。 必须先结束对文件的所有处理，然后才能删除文件。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**remove**|\<stdio.h> 或 \<io.h>|
|**_wremove**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_remove.c
/* This program uses remove to delete crt_remove.txt */

#include <stdio.h>

int main( void )
{
   if( remove( "crt_remove.txt" ) == -1 )
      perror( "Could not delete 'CRT_REMOVE.TXT'" );
   else
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );
}
```

### <a name="input-crtremovetxt"></a>输入：crt_remove.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>示例输出

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
