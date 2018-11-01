---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488109"
---
# <a name="tmpfiles"></a>tmpfile_s

创建临时文件。 它是 [tmpfile](tmpfile.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>参数

*pFilePtr*<br/>
指针地址，用于存储生成的指向流的指针的地址。

## <a name="return-value"></a>返回值

如果成功，则返回 0；如果失败，则为错误代码。

### <a name="error-conditions"></a>错误条件

|*pFilePtr*|**返回值**|**内容***pFilePtr* |
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|未更改|

如果出现以上参数验证错误，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL**和返回值是**EINVAL**。

## <a name="remarks"></a>备注

**Tmpfile_s**函数创建临时文件，并将指针放在该流*pFilePtr*参数。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam_s](tmpnam-s-wtmpnam-s.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](fopen-wfopen.md) 结合使用。

如果无法打开该文件， **tmpfile_s**写入**NULL**到*pFilePtr*参数。 通常情况下，或当终止时关闭该文件时，会自动删除此临时文件 **_rmtmp**调用，假定当前工作目录不会更改。 在打开临时文件时**w + b** （二进制读/写） 模式。

如果你尝试，则会发生故障超过**TMP_MAX_S** （请参阅 STDIO。使用 H） 调用**tmpfile_s**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

> [!NOTE]
> 此示例中可能需要管理权限才能在 Windows 上运行。

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
