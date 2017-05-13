---
title: "tmpfile | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpfile
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
- tmpfile
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: 21
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
ms.openlocfilehash: efb6cd7868a393d4c946382c59b071de138ff55b
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="tmpfile"></a>tmpfile
创建临时文件。 此函数已弃用，因为已提供更为安全的版本；请参阅 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
FILE *tmpfile( void );  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `tmpfile` 返回流指针。 否则，返回 `NULL` 指针。  
  
## <a name="remarks"></a>备注  
 `tmpfile` 函数创建临时文件并返回指向该流的指针。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](../../c-runtime-library/reference/fopen-wfopen.md) 结合使用。  
  
 如果文件无法打开，则 `tmpfile` 返回 `NULL` 指针。 当文件关闭、程序正常终止或调用 `_rmtmp` 时，此临时文件将被自动删除（假定当前工作目录未更改）。 临时文件在 `w+b`（二进制读/写）模式下打开。  
  
 如果尝试使用 `tmpfile` 执行超过 TMP_MAX 次调用（请参阅 STDIO.H），则可能失败。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`tmpfile`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
> [!NOTE]
>  此示例需要在 Windows Vista 上运行的管理员特权。  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
```Output  
Temporary file 1 was created  
Temporary file 2 was created  
Temporary file 3 was created  
3 temporary files deleted  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)
