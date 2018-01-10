---
title: "fgetpos | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fgetpos
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
f1_keywords: fgetpos
dev_langs: C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 418de3c365c2c42c1cfc41d386a1a823d7e8cfad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fgetpos"></a>fgetpos
获取流的文件位置指示器。  
  
## <a name="syntax"></a>语法  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 目标流。  
  
 `pos`  
 位置指示器存储。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `fgetpos` 返回 0。 失败时，它返回一个非零值，并将 `errno` 设置为下列任一清单常量（在 STDIO.H 中定义）：`EBADF` 或 `EINVAL`，前者意味着指定流不是有效文件指针或不可访问，后者意味着 `stream` 值或 `pos` 值无效，例如，如果任意一个为 null 指针。 如果 `stream` 或 `pos` 为 `NULL` 指针，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
## <a name="remarks"></a>备注  
 `fgetpos` 函数获取 `stream` 参数的文件位置指示器的当前值，并将其存储在 `pos` 指向的对象中。 `fsetpos` 函数可以稍后使用存储在 `pos` 中的信息来重置在调用 `fgetpos` 时 `stream` 参数的指针所指向的位置。 `pos` 值以内部格式存储，且仅供 `fgetpos` 和 `fsetpos` 使用。  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fgetpos`|\<stdio.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
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
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### <a name="output-crtfgetpostxt"></a>输出：crt_fgetpos.txt  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)