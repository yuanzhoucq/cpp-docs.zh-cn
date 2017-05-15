---
title: "fseek、_fseeki64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseeki64
- fseek
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
apitype: DLLExport
f1_keywords:
- fseek
- _fseeki64
dev_langs:
- C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0d0c0bf620f1b89b9decceed3db9434dae4f9437
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="fseek-fseeki64"></a>fseek、_fseeki64
将文件指针移到指定位置。  
  
## <a name="syntax"></a>语法  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `offset`  
 `origin` 中的字节数。  
  
 `origin`  
 初始位置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `fseek` 和 `_fseeki64` 返回 0。 否则，返回一个非零值。 在无法查找的设备上，返回值是未定义的。 如果 `stream` 为 null 指针，或 `origin` 不是下述所允许的值之一，则 `fseek` 和 `_fseeki64` 将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
## <a name="remarks"></a>备注  
 `fseek`和`_fseeki64`函数与关联的文件指针 （如果有） 的移动`stream`到的新位置`offset`个字节从`origin`。 该流上的下一步操作发生在新位置。 在准备更新的流上，下一个操作可以是读取或写入。 参数源必须是 STDIO.H 中定义的以下常量之一：  
  
 `SEEK_CUR`  
 文件指针的当前位置。  
  
 `SEEK_END`  
 文件结尾。  
  
 `SEEK_SET`  
 文件开头。  
  
 可以使用 `fseek` 和 `_fseeki64` 在文件的任何位置重新定位指针。 此外还可以在文件结尾外放置指针。 `fseek`和`_fseeki64`清除文件尾指示器，并且不具备任何之前的效果`ungetc`调用针对`stream`。  
  
 当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入的位置确定。 如果在为追加而打开的文件中尚未发生 I/O 操作，则文件位置是文件开头。  
  
 在文本模式下打开的流的`fseek`和`_fseeki64`用途相当有限，因为回车换行符翻译可能会导致`fseek`和`_fseeki64`以产生意外的结果。 唯一`fseek`和`_fseeki64`保证在文本模式下打开的流处理的操作︰  
  
-   使用相对于任何原始值的偏移 0 进行查找。  
  
-   查找从开始处的偏移量值的文件返回到调用`ftell`时使用`fseek`或`_ftelli64`时使用`_fseeki64`。  
  
 此外，在文本模式中，CTRL+Z 将在输入时解释为文件结尾字符。 在打开以进行读取/写入的文件中，`fopen` 和所有相关例程将检查文件末尾的 Ctrl+Z 并在可能的情况下将其移除。 由于结合使用了 `fseek` 和 `ftell`，或 `_fseeki64` 和 `_ftelli64`，可执行此操作。在以 CTRL+Z 结尾的文件中移动可能导致 `fseek` 或 `_fseeki64` 在文件末尾附近无法正常工作。  
  
 当 CRT 打开以字节顺序标记 (BOM) 开头的文件时，文件指针位于 BOM 后面（即，位于文件实际内容的开头）。 如果需要 `fseek` 文件开头，请使用 `ftell` 来获取初始位置并对其执行 `fseek` 而不是对位置 0。  
  
 此函数在执行期间将锁定其他线程，因此是线程安全的。 有关非锁定版本，请参阅 [_fseek_nolock、_fseeki64_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fseek`|\<stdio.h>|  
|`_fseeki64`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
```Output  
File pointer is set to middle of first line.  
This is the file 'fseek.out'.  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell、_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek、_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)
