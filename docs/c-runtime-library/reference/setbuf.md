---
title: setbuf | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- setbuf
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
- setbuf
dev_langs:
- C++
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7a88ac98b8226b51ad036a0e31c919db9a63a0a0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="setbuf"></a>setbuf

控制流缓冲。 此函数已弃用；请改用 [setvbuf](setvbuf.md)。

## <a name="syntax"></a>语法

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>参数

*流*指向**文件**结构。

*缓冲区*用户分配的缓冲区。

## <a name="remarks"></a>备注

**Setbuf**函数控制缓冲为*流*。 *流*参数必须引用未读取或写入打开的文件。 如果*缓冲区*自变量是**NULL**，流是无缓冲。 如果不是，缓冲区必须指向长度的字符数组**BUFSIZ**，其中**BUFSIZ**中 STDIO 定义是缓冲区大小。H。 用户指定的缓冲区（而不是给定流的默认系统分配的缓冲区）用于 I/O 缓存。 **Stderr**流是无缓冲默认情况下，但你可以使用**setbuf**要分配到的缓冲区**stderr**。

**setbuf**已被取代[setvbuf](setvbuf.md)，对于新代码的首选例程。 **setbuf**保留用于与现有代码兼容。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
