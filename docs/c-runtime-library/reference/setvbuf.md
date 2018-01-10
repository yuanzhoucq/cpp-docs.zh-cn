---
title: "setvbuf | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: setvbuf
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
f1_keywords: setvbuf
dev_langs: C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0855982627c60c51ec5753031ae932ffd430f024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setvbuf"></a>setvbuf
控制流缓冲和缓冲区大小。  
  
## <a name="syntax"></a>语法  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `buffer`  
 用户分配的缓冲区。  
  
 `mode`  
 缓冲模式。  
  
 `size`  
 缓冲区大小（以字节为单位）。 允许的范围：2 <= `size` <= INT_MAX (2147483647)。 在内部将为 `size` 提供的值向下舍入为最接近的 2 的倍数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。  
  
 如果 `stream` 为 `NULL`，或如果 `mode` 或 `size` 不在有效更改之内，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `setvbuf` 函数允许程序控制 `stream` 的缓冲和缓冲区大小。 `stream` 必须引用自该文件打开后尚未进行 I/O 操作的打开文件。 将 `buffer` 所指向的数组用作缓冲区，除非它是 `NULL`，在这种情况下，`setvbuf` 使用长度为 `size`/2 * 2 字节的自动分配的缓冲区。  
  
 此模式必须是 `_IOFBF`、`_IOLBF` 或 `_IONBF`。 如果 `mode` 是 `_IOFBF` 或 `_IOLBF`，则将 `size` 用作缓冲区的大小。 如果 `mode` 是 `_IONBF`，则该流取消缓冲并忽略 `size` 和 `buffer`。 `mode` 的值及其含义是：  
  
 `_IOFBF`  
 完全缓冲；也就是说，将 `buffer` 用作缓冲区并将 `size` 用作缓冲区的大小。 如果 `buffer` 是 `NULL`，则使用长度为 `size` 字节的自动分配的缓冲区。  
  
 `_IOLBF`  
 对于某些系统，会提供行缓冲。 但是，对于 Win32，该行为与 `_IOFBF` 完全缓冲一样。  
  
 `_IONBF`  
 将不会使用缓冲区，无论 `buffer` 或 `size`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`setvbuf`|\<stdio.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
```Output  
'stream1' now has a buffer of 1024 bytes  
'stream2' now has no buffer  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)