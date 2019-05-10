---
title: fgetpos
ms.date: 11/04/2016
apiname:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: e213c9830ffe6edf04b12a80828f14cc48f77524
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333925"
---
# <a name="fgetpos"></a>fgetpos

获取流的文件位置指示器。

## <a name="syntax"></a>语法

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>参数

*stream*<br/>
目标流。

*pos*<br/>
位置指示器存储。

## <a name="return-value"></a>返回值

如果成功， **fgetpos**返回 0。 在失败时，它返回非零值，并设置**errno**下列任一清单常量 （在 STDIO 中定义。H):**EBADF**，这意味着指定的流不是有效的文件指针或不可访问，或**EINVAL**，这意味着*流*的值或值*pos*是无效的例如，如果可以为 null 指针。 如果*流*或*pos*是**NULL**指针，该函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>备注

**Fgetpos**函数获取的当前值*流*参数的文件位置指示符和存储它的对象中指向*pos*。**Fsetpos**函数可以稍后使用信息存储在*pos*若要重置*流*参数的指针，指向其位置时**fgetpos**调用。 *Pos*值以内部格式存储，并适用于使用仅由**fgetpos**并**fsetpos**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetpostxt"></a>输入：crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>输出：crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
