---
title: _makepath、_wmakepath | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6ad1331021331e9c9ddc1d1344aae8ed164ce2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="makepath-wmakepath"></a>_makepath、_wmakepath

从组件创建路径名。 提供这些函数的更多安全版本；请参阅 [_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)。

## <a name="syntax"></a>语法

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>参数

*路径*完整路径缓冲区。

*驱动器*包含字母 （A、 B 和等等） 对应于所需的驱动器和可选的尾随冒号。 **_makepath**如果缺少会自动插入复合路径中的冒号。 如果*驱动器*是**NULL**或指向空字符串，无驱动器号显示在复合*路径*字符串。

*dir*包含路径的目录，不包括驱动器指示符或实际文件名。 尾随斜杠是可选的并请正斜杠 （/） 或反斜杠 (\\) 或两者可能使用在单个*dir*自变量。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果*dir*是**NULL**或指向空字符串，没有目录路径插入在复合*路径*字符串。

*fname*包含无任何文件扩展名的基文件名。 如果*fname*是**NULL**或指向空字符串，任何文件名插入在复合*路径*字符串。

*ext*包含实际的文件扩展名，有或没有前导句点 （.）。 **_makepath**自动插入句点，如果未出现在*ext*。如果*ext*是**NULL**或指向空字符串，无扩展名插入在复合*路径*字符串。

## <a name="remarks"></a>备注

**_Makepath**函数从各个组件，将结果存储在中创建复合路径字符串*路径*。 *路径*可能包括驱动器号、 目录路径、 文件名和文件扩展名。 **_wmakepath**是宽字符版本的 **_makepath**; 的自变量 **_wmakepath**是宽字符字符串。 **_wmakepath**和 **_makepath**否则具有相同行为。

**安全说明** 使用以 null 结尾的字符串。 若要避免缓冲区溢出，以 null 结尾的字符串不得超过的大小*路径*缓冲区。 **_makepath**不确保复合路径字符串的长度不超过 **_MAX_PATH**。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路径*自变量必须指向足以容纳完整路径的空缓冲区。 复合*路径*必须不大于 **_MAX_PATH**常量，在 Stdlib.h 中定义。

如果路径是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 此外， **errno**设置为**EINVAL**。 **NULL**所有其他参数的允许值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)<br/>
