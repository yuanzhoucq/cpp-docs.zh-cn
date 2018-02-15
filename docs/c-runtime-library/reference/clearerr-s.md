---
title: "clearerr_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- clearerr_s
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
- clearerr_s
dev_langs:
- C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84cb2b30ccf074812dde52f103c22df04ed7d52d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="clearerrs"></a>clearerr_s
重置流的错误指示符。 这是 [clearerr](../../c-runtime-library/reference/clearerr.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t clearerr_s(  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回零；如果 `stream` 为 NULL，则返回 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `clearerr_s` 函数为 `stream` 重置错误指示符和文件尾指示符。 不会自动清除错误指示符；设置指定流的错误指示符后，在调用 `clearerr_s`、`clearerr`、`fseek`、`fsetpos` 或 `rewind` 前，将继续在该流上执行操作以返回错误值。  
  
 如果 `stream` 为 NULL，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`clearerr_s`|\<stdio.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_clearerr_s.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   errno_t err;  
  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
}  
```  
  
```Output  
  
n  
  
```  
  
```Output  
  
      nWrite error: Bad file descriptor  
Will input cause an error? n  
```  
  
## <a name="see-also"></a>请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)