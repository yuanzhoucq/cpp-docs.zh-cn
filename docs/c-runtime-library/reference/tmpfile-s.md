---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 48c599887a8a903d52c7dcd46b98046119c9d3ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919931"
---
# <a name="tmpfile_s"></a>tmpfile_s

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

|*pFilePtr*|**返回值**|*PFilePtr* **的内容**  |
|----------------|----------------------|---------------------------------|
|**Null**|**EINVAL**|未更改|

如果出现以上参数验证错误，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且返回值为**EINVAL**。

## <a name="remarks"></a>备注

**Tmpfile_s**函数将创建一个临时文件，并在*pFilePtr*参数中放置一个指向该流的指针。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam_s](tmpnam-s-wtmpnam-s.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](fopen-wfopen.md) 结合使用。

如果文件无法打开， **tmpfile_s**会将**NULL**写入*pFilePtr*参数。 当文件关闭、程序正常终止时，或在调用 **_rmtmp**时，如果当前工作目录未更改，则会自动删除此临时文件。 临时文件以**w + b** （二进制读取/写入）模式打开。

如果尝试的**TMP_MAX_S 超过**（请参阅 stdio.h。H）对**tmpfile_s**调用。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

> [!NOTE]
> 此示例可能需要管理权限才能在 Windows 上运行。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
