---
title: _makepath_s、_wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341607"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s、_wmakepath_s

从组件创建路径名。 这些版本的 [_makepath、_wmakepath](makepath-wmakepath.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>参数

*路径*<br/>
完整路径缓冲区。

*大小字内*<br/>
缓冲区大小（以单词为单位）。

*大小字节*<br/>
缓冲区的大小（以字节为单位）。

*驱动*<br/>
包含一个与所需的驱动器对应的字母（A、B 等）和可选的尾随冒号。 如果缺少冒号 **，_makepath_s**会自动在复合路径中插入冒号。 如果*驱动器*为**NULL**或指向空字符串，则复合*路径*字符串中不会显示驱动器号。

*dir*<br/>
包含目录路径，但不包括驱动器指示符或实际文件名。 尾随斜杠是可选的，在单个*dir*参数中可以使用前斜杠\\（/） 或反斜杠 （） 或两者。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果*dir*为**NULL**或指向空字符串，则复合路径字符串中未插入任何目录*路径*。

*fname*<br/>
包含无任何文件扩展名的基文件名。 如果*fname*为**NULL**或指向空字符串，则复合*路径*字符串中未插入任何文件名。

*内线*<br/>
包含实际的文件扩展名（带有或不带前导句点 (.)）。 如果期间未显示在*分机*中 **，_makepath_s**自动插入该期间。如果*分机*为**NULL**或指向空字符串，则复合*路径*字符串中不会插入任何扩展。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

### <a name="error-conditions"></a>错误条件

|*路径*|*大小以* / *字节为单位*|返回|*路径*内容|
|------------|------------------------------------|------------|------------------------|
|**空**|any|**埃因瓦尔**|未修改|
|any|<= 0|**埃因瓦尔**|未修改|

如果发生任何以上错误情况，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续 **，errno**设置为**EINVAL，** 函数返回**EINVAL**。 **允许参数***驱动器**、fname*和*ext*的 NULL。有关这些参数为空指针或空字符串时的行为的信息，请参阅备注部分。

## <a name="remarks"></a>备注

**_makepath_s**函数从单个组件创建复合路径字符串，将结果存储在*路径*中。 *路径*可能包括驱动器号、目录路径、文件名和文件名扩展名。 **_wmakepath_s**是 **_makepath_s**的宽字符版本;要 **_wmakepath_s**的参数是宽字符字符串。 **_wmakepath_s****和_makepath_s**行为相同。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*路径*参数必须指向足够大以容纳完整路径的空缓冲区。 复合*路径*不能大于在 Stdlib.h 中定义的 **_MAX_PATH**常量。

如果路径为**NULL，** 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 此外 **，errno**设置为**EINVAL**。 所有其他参数都允许**NULL**值。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
