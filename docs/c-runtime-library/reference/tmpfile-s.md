---
title: "tmpfile_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpfile_s
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
- tmpfile_s
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
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
ms.openlocfilehash: e66ffa5fdbb1785191865eba92c9d673fb847ada
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="tmpfiles"></a>tmpfile_s
创建临时文件。 它是 [tmpfile](../../c-runtime-library/reference/tmpfile.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pFilePtr`  
 指针地址，用于存储生成的指向流的指针的地址。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0；如果失败，则为错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`pFilePtr`|**返回值**|`pFilePtr` **的内容**|  
|----------------|----------------------|---------------------------------|  
|`NULL`|`EINVAL`|未更改|  
  
 如果出现以上参数验证错误，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL`，且返回值为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `tmpfile_s` 函数创建临时文件，并在 `pFilePtr` 参数中将指针放入该流。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) 或 [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](../../c-runtime-library/reference/fopen-wfopen.md) 结合使用。  
  
 如果文件无法打开，则 `tmpfile_s` 将 `NULL` 写入到 `pFilePtr` 参数。 当文件关闭、程序正常终止或调用 `_rmtmp` 时，此临时文件将被自动删除（假定当前工作目录未更改）。 临时文件在 `w+b`（二进制读/写）模式下打开。  
  
 如果尝试使用 `tmpfile_s.` 执行超过 `TMP_MAX_S` 次调用（请参阅 STDIO.H），则可能失败  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`tmpfile_s`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
> [!NOTE]
>  此示例需要在 Windows Vista 上运行的管理员特权。  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
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
