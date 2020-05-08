---
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
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
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 40f23db88abf9733eada9e775aacda83cba5829a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910336"
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

*流*<br/>
指向**文件**结构的指针。

*宽限*<br/>
用户分配的缓冲区。

## <a name="remarks"></a>备注

**Setbuf**函数控制*对流*的缓冲。 *流*参数必须引用未读取或写入的打开文件。 如果*缓冲区*参数为**NULL**，则流未缓冲。 如果不是，则缓冲区必须指向长度为**BUFSIZ**的字符数组，其中**BUFSIZ**是 stdio.h 中定义的缓冲区大小。高. 用户指定的缓冲区（而不是给定流的默认系统分配的缓冲区）用于 I/O 缓存。 默认情况下， **stderr**流是无缓冲的，但您可以使用**setbuf**为**stderr**分配缓冲区。

**setbuf**已替换为[setvbuf](setvbuf.md)，这是新代码的首选例程。 与**setvbuf**不同， **setbuf**无法报告错误。 **setvbuf**还允许同时控制缓冲模式和缓冲区大小。 存在**setbuf** ，以便与现有代码兼容。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
