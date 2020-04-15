---
title: rename、_wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- _wrename
- _trename
- Rename
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338105"
---
# <a name="rename-_wrename"></a>rename、_wrename

重命名文件或目录。

## <a name="syntax"></a>语法

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>参数

*oldname*<br/>
指向旧名称的指针。

*新名称*<br/>
指向新名称的指针。

## <a name="return-value"></a>返回值

如果成功，则这些函数均返回 0。 在错误时，函数返回一个非零值，并将**errno**设置到以下值之一：

|errno 值|条件|
|-|-|
| **EACCES** | 由 *newname* 指定的文件或目录已存在或无法创建（路径无效）；或 *oldname* 是目录，但 *newname* 指定了不同路径。 |
| **埃诺恩特** | 未找到由 *oldname* 指定的文件或路径。 |
| **埃因瓦尔** | 名称包含无效字符。 |

有关其他可能的返回值，请参阅 [_doserrno、_errno、syserrlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**rename** 函数将 *oldname* 指定的文件或目录重命名为由 *newname* 给定的名称。 旧名称必须是现有文件或目录的路径。 新名称一定不能是现有文件或目录的名称。 通过在 *newname* 参数中给定不同的路径，可以使用 **rename** 将文件从一个目录或设备移至另一个目录或设备。 但是，不能使用 **rename** 来移动目录。 目录可以重命名，但不能移动。

**_wrename**是 **_rename**的宽字符版本;要 **_wrename**的参数是宽字符字符串。 **_wrename**和 **_rename**行为相同。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**重 命名**|**重 命名**|**_wrename**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**重 命名**|\<io.h> 或 \<stdio.h>|
|**_wrename**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>输出

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
