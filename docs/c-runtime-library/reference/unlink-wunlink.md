---
title: _unlink、_wunlink
ms.date: 11/04/2016
apiname:
- _unlink
- _wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: ec59a02f1302fe4a2149889cf1b48090d061d6b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268767"
---
# <a name="unlink-wunlink"></a>_unlink、_wunlink

删除文件。

## <a name="syntax"></a>语法

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>参数

*filename*<br/>
要删除的文件名称。

## <a name="return-value"></a>返回值

如果成功，则这些函数均返回 0。 否则，该函数返回-1 并设置**errno**到**EACCES**，表示路径指定只读文件或目录，或设置为**ENOENT**，这意味着，文件或路径未找到。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Unlink**函数将删除指定的文件*filename*。 **_wunlink**是宽字符版本 **_unlink**; *filename*参数 **_wunlink**是宽字符字符串。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_unlink**|\<io.h> 和 \<stdio.h>|
|**_wunlink**|\<io.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="code-example"></a>代码示例

此程序使用 _unlink 删除 CRT_UNLINK.TXT。

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crtunlinktxt"></a>输入：crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>示例输出

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove、_wremove](remove-wremove.md)<br/>
