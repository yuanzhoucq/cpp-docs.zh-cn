---
title: _fileno
ms.date: 4/2/2020
api_name:
- _fileno
- _o__fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: 0ac0a8d2cf4185dab0aa3d335c16cf89da58c7a6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919474"
---
# <a name="_fileno"></a>_fileno

获取与流关联的文件描述符。

## <a name="syntax"></a>语法

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**_fileno**返回文件描述符。 无错误返回。 如果*stream*未指定打开的文件，则结果是不确定的。 如果 stream 为**NULL**， **_fileno**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 errno 设置为 EINVAL********。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

> [!NOTE]
> 如果**stdout**或**stderr**不与输出流（例如，在没有控制台窗口的 Windows 应用程序中）关联，则返回的文件描述符为-2。 在早期版本中，返回的文件说明符为 -1。 此更改使应用程序得以将此情况与错误区分开来。

## <a name="remarks"></a>备注

**_Fileno**例程返回当前与*stream*关联的文件说明符。 此例程作为函数和宏实现。 有关选择任一实现的信息，请参阅[在函数和宏之间选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
