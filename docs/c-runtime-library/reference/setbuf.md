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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f96cffb8770cda78ebff8d873b441ddc288bc41f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332081"
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

*缓冲区*<br/>
用户分配的缓冲区。

## <a name="remarks"></a>备注

**setbuf**函数控制*流的*缓冲。 *流*参数必须引用尚未读取或写入的打开文件。 如果*缓冲区*参数为**NULL，** 则流将取消缓冲。 如果不是，缓冲区必须指向长度**为 BUFSIZ**的字符数组，其中**BUFSIZ**是 STDIO 中定义的缓冲区大小。H。 用户指定的缓冲区（而不是给定流的默认系统分配的缓冲区）用于 I/O 缓存。 默认情况下，**斯特值流**未缓冲，但您可以使用**setbuf**将缓冲区分配给**更稳。**

**setbuf**已被[setvbuf](setvbuf.md)替换，这是新代码的首选例程。 与**setvbuf**不同 **，setbuf**无法报告错误。 **setvbuf**还允许您控制缓冲模式和缓冲区大小。 **setbuf**存在是为了与现有代码兼容。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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
