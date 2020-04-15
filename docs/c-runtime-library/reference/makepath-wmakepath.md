---
title: _makepath、_wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341583"
---
# <a name="_makepath-_wmakepath"></a>_makepath、_wmakepath

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

*路径*<br/>
完整路径缓冲区。

*驱动*<br/>
包含一个与所需的驱动器对应的字母（A、B 等）和可选的尾随冒号。 **_makepath**如果缺少冒号，则会自动在复合路径中插入冒号。 如果*驱动器*为**NULL**或指向空字符串，则复合*路径*字符串中不会显示驱动器号。

*dir*<br/>
包含目录路径，但不包括驱动器指示符或实际文件名。 尾随斜杠是可选的，在单个*dir*参数中可以使用前斜杠\\（/） 或反斜杠 （） 或两者。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果*dir*为**NULL**或指向空字符串，则复合路径字符串中未插入任何目录*路径*。

*fname*<br/>
包含无任何文件扩展名的基文件名。 如果*fname*为**NULL**或指向空字符串，则复合*路径*字符串中未插入任何文件名。

*内线*<br/>
包含实际的文件扩展名（带有或不带前导句点 (.)）。 如果期间未显示在*分机*中 **，_makepath**自动插入期间。如果*分机*为**NULL**或指向空字符串，则复合*路径*字符串中不会插入任何扩展。

## <a name="remarks"></a>备注

**_makepath**函数从单个组件创建复合路径字符串，将结果存储在*路径*中。 *路径*可能包括驱动器号、目录路径、文件名和文件名扩展名。 **_wmakepath**是 **_makepath**的宽字符版本;要 **_wmakepath**的参数是宽字符字符串。 **_wmakepath**和 **_makepath**行为相同。

**安全说明** 使用以 null 结尾的字符串。 为了避免缓冲区溢出，null 终止字符串不得超过*路径*缓冲区的大小。 **_makepath**不确保复合路径字符串的长度不超过 **_MAX_PATH**。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路径*参数必须指向足够大以容纳完整路径的空缓冲区。 复合*路径*不能大于在 Stdlib.h 中定义的 **_MAX_PATH**常量。

如果路径为**NULL，** 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 此外 **，errno**设置为**EINVAL**。 所有其他参数都允许**NULL**值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)<br/>
