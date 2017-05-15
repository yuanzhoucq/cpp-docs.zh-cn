---
title: "_flushall | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _flushall
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
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 230d52cf98e7dc563ea5d0067de7df31af8549f9
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="flushall"></a>_flushall
刷新所有流；清除所有缓冲区。  
  
## <a name="syntax"></a>语法  
  
```  
int _flushall( void );  
```  
  
## <a name="return-value"></a>返回值  
 `_flushall` 返回打开的流（输入和输出）的数量。 无错误返回。  
  
## <a name="remarks"></a>备注  
 默认情况下，`_flushall` 函数会向相应的文件中写入与打开的输出流关联所有缓冲区的内容。 与打开的输入流关联的所有缓冲区的当前内容将被清除。 （这些缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。）  
  
 如果在调用 `_flushall` 后进行读取，则会将输入文件中的新数据读取到缓冲区中。 在调用 `_flushall` 后，所有流将保持打开状态。  
  
 利用运行库的提交到磁盘功能，您可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 Commode.obj 链接来启用此功能。 在生成的可执行文件中，调用 `_flushall` 会将所有缓冲区的内容写入磁盘中。 仅 `_flushall` 和 `fflush` 受 Commode.obj 的影响。  
  
 有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](../../c-runtime-library/reference/fopen-wfopen.md) 和 [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_flushall`|\<stdio.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
```Output  
There were 3 streams flushed  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_commit](../../c-runtime-library/reference/commit.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)
