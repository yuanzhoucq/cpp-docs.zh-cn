---
title: "fflush | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fflush
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
- fflush
dev_langs:
- C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23d90b61862736fc97c18343fe82f8ccf3aa42b5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fflush"></a>fflush
刷新流。  
  
## <a name="syntax"></a>语法  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果已成功刷新缓冲区，`fflush` 将返回 0。 在指定流无缓冲区或处于打开状态以仅供读取的情况下，也会返回值 0。 返回值 `EOF` 指示一个错误。  
  
> [!NOTE]
>  如果 `fflush` 返回 `EOF`，数据可能已经因写入失败而丢失。 设置一个严重错误的处理程序时，通过 `setvbuf` 函数或使用低级别 I/O 例程（如`_open`、`_close`，和`_write`）而不是流 I/O 函数来关闭缓冲最安全。  
  
## <a name="remarks"></a>备注  
 `fflush` 函数刷新流 `stream`。 如果以写入模式打开流，或者以更新模式打开并且最后一个操作是写入，则流缓冲区的内容会被写入到基础文件，否则设备和缓冲区将被丢弃。 如果在读取模式下打开流或流并不具有缓冲区，则对 `fflush` 的调用不起任何作用，且不保留任何缓冲区。 调用 `fflush` 会使任何以前对流的 `ungetc` 的调用无效。 调用后，该流保持打开状态。  
  
 如果 `stream` 是 `NULL`，则行为与每个打开流上对 `fflush` 的调用一致。 最后一次操作是写入的所有以写入模式打开的流以及所有以更新模式打开的流都将被刷新。 调用对其他流无效。  
  
 缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。 利用运行时库的提交到磁盘功能，可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 COMMODE.OBJ 链接来启用此功能。 在生成的可执行文件中，调用 `_flushall` 会将所有缓冲区的内容写入磁盘中。 仅 `_flushall` 和 `fflush` 受 COMMODE.OBJ 的影响。  
  
 有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](../../c-runtime-library/reference/fopen-wfopen.md) 和 [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
 此函数会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 `_fflush_nolock`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fflush`|\<stdio.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
```Output  
  
      This is a test  
This is a test  
  
```  
  
```Output  
  
      This is a test  
This is a testEnter a sentence of four words with scanf: This is a test  
This  
is  
a  
test  
Enter the same sentence with gets: This is a test  
This is a test  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)