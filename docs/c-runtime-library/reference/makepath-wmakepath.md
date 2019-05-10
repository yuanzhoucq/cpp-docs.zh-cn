---
title: _makepath、_wmakepath
ms.date: 11/04/2016
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
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: 073f8aba6936aa33dafcef7ed47f5286802a4948
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285694"
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

*path*<br/>
完整路径缓冲区。

*drive*<br/>
包含一个与所需的驱动器对应的字母（A、B 等）和可选的尾随冒号。 **_makepath**缺少时自动插入复合路径中的冒号。 如果*驱动器*是**NULL**或指向空字符串，无驱动器号出现在复合*路径*字符串。

*dir*<br/>
包含目录路径，但不包括驱动器指示符或实际文件名。 尾随斜杠是可选的并且是正斜杠 （/） 或反斜杠 (\\) 或两者可能使用在单个*dir*参数。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果*dir*是**NULL**或为空字符串，没有目录路径的点插入在复合*路径*字符串。

*fname*<br/>
包含无任何文件扩展名的基文件名。 如果*fname*是**NULL**或指向空字符串，任何文件名插入在复合*路径*字符串。

*ext*<br/>
包含实际的文件扩展名（带有或不带前导句点 (.)）。 **_makepath**如果未出现在自动插入句点*ext*。如果*ext*是**NULL**或为空字符串，不扩展点插入在复合*路径*字符串。

## <a name="remarks"></a>备注

**_Makepath**函数从各个组件，将结果存储在中创建复合路径字符串*路径*。 *路径*可能包括驱动器号、 目录路径、 文件名和文件扩展名。 **_wmakepath**是宽字符版本 **_makepath**; 的自变量 **_wmakepath**都是宽字符字符串。 **_wmakepath**并 **_makepath**行为相同。

**安全说明** 使用以 null 结尾的字符串。 若要避免缓冲区溢出，以 null 结尾的字符串不能超过的大小*路径*缓冲区。 **_makepath**不能确保复合路径字符串的长度不超过 **_MAX_PATH**。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路径*自变量必须指向空缓冲区足够大以保存的完整路径。 复合*路径*必须为不大于 **_MAX_PATH**在 Stdlib.h 中定义的常量。

如果路径是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 此外， **errno**设置为**EINVAL**。 **NULL**所有其他参数的允许值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
