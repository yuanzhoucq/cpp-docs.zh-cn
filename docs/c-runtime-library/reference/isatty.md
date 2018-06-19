---
title: _isatty | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isatty
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
- _isatty
dev_langs:
- C++
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4be35fce0a790751683a4bf8a0cceaf938fea82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402454"
---
# <a name="isatty"></a>_isatty

确定一个文件描述符是否与字符设备相关联。

## <a name="syntax"></a>语法

```C
int _isatty( int fd );
```

### <a name="parameters"></a>参数

*fd*<br/>
引用设备以进行测试的文件说明符。

## <a name="return-value"></a>返回值

**_isatty**返回非零值，如果该描述符不与字符设备相关联。 否则为 **_isatty**返回 0。

## <a name="remarks"></a>备注

**_Isatty**函数将确定是否*fd*与字符设备 （终端、 控制台、 打印机或串行端口） 相关联。

此函数验证*fd*参数。 如果*fd*是错误的文件指针，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回 0 并设置**errno**到**EBADF**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_isatty**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>示例输出

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
