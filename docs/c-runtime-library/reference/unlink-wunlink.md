---
title: _unlink、_wunlink
ms.date: 11/04/2016
api_name:
- _unlink
- _wunlink
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 878a1b4aa009bc8528dfac1908ed26c7e3b269ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957394"
---
# <a name="_unlink-_wunlink"></a>_unlink、_wunlink

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

如果成功，则这些函数均返回 0。 否则，该函数将返回-1 并将**errno**设置为**EACCES**，这意味着路径指定了只读文件或目录，或**ENOENT**，这意味着找不到文件或路径。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Unlink**函数删除*filename*指定的文件。 **_wunlink**是 **_unlink**的宽字符版本; **_wunlink**的*filename*参数是宽字符字符串。 否则这些函数具有相同行为。

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

### <a name="input-crt_unlinktxt"></a>输入：crt_unlink.txt

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
