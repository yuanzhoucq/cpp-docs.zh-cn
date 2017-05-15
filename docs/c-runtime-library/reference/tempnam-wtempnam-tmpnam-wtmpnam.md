---
title: "_tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 20
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
ms.openlocfilehash: 0600d44b2b87ed3bb56e7d1c64fffd762e77aff2
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam
生成可用于创建临时文件的名称。 提供这些函数的更多安全版本；请参阅 [tmpnam_s、_wtmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### <a name="parameters"></a>参数  
 `prefix`  
 将在由 `_tempnam` 返回的名称前面附加的字符串。  
  
 `dir`  
 文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。  
  
 `str`  
 指针将保留生成的名称，该名称将与函数所返回的名称相同。 这是保存生成的名称的简便方法。  
  
## <a name="return-value"></a>返回值  
 如果失败，则每个函数均返回一个指向生成的名称的指针或 `NULL`。 如果你尝试，则可能发生失败多个`TMP_MAX`（请参阅 STDIO。H） 使用调用`tmpnam`或如果你使用`_tempnam`且存在 TMP 环境变量在和中指定了无效的目录名称`dir`参数。  
  
> [!NOTE]
>  由 `tmpnam` 和 `_wtmpnam` 返回的指针指向内部静态缓冲区。 不应调用 [free](../../c-runtime-library/reference/free.md) 来释放这些指针。 对于由 `_tempnam` 和 `_wtempnam` 分配的指针，需要调用 `free`。  
  
## <a name="remarks"></a>备注  
 这些函数返回的文件名当前不存在。 `tmpnam` 返回当前工作目录中唯一的名称，而 `_tempnam` 允许你在目录中生成当前名称以外的唯一名称。 请注意，如果一个文件名称使用反斜杠作为前缀（如 \fname21），表示该名称对当前工作目录有效。  
  
 对于 `tmpnam`，可以在 `str` 中存储生成的此文件名。 如果 `str` 为 `NULL`，则 `tmpnam` 将结果留在内部静态缓冲区中。 因此，任何后续调用都会破坏该值。 由 `tmpnam` 生成的名称包含程序生成的文件名以及第一次调用`tmpnam` 后，基数 32 中的连续数字的文件扩展名（当 STDIO.H 中的 `TMP_MAX` 为 32,767 时，扩展名为 .1-.vvu）。  
  
 `_tempnam` 将按以下规则，为所选目录生成唯一文件名：  
  
-   如果定义了 TMP 环境变量并将其设置为有效的目录名称，则 TMP 所指定的目录将生成唯一文件名。  
  
-   如果未定义 TMP 环境变量，或为其设置了不存在的目录名称，则 `_tempnam` 将 `dir` 参数用作生成唯一名称的路径。  
  
-   如果未定义 TMP 环境变量，或为其设置了并不存在的目录名称，且如果 `dir` 为 `NULL` 或被设置为不存在的目录名称，则 `_tempnam` 将使用当前工作目录生成唯一名称。 目前，如果 TMP 和 `dir` 所指定的目录的名称不存在，则 `_tempnam` 函数调用将失败。  
  
 由 `_tempnam` 返回的名称将是 `prefix` 和顺序号的串联的组合，为指定目录创建唯一的文件名。 `_tempnam` 生成无扩展名的文件名。 `_tempnam` 使用 [malloc](../../c-runtime-library/reference/malloc.md) 为文件名分配空间；程序负责在不再需要此空间时将其释放。  
  
 `_tempnam` 和 `tmpnam` 将根据情况自动处理多字节字符串参数，从而根据从操作系统获取的 OEM 代码页识别多字节字符序列。 `_wtempnam` 是 `_tempnam` 的宽字符版本；`_wtempnam` 的参数和返回值都是宽字符字符串。 `_wtempnam` 和 `_tempnam` 的行为方式相同，只不过 `_wtempnam` 不处理多字节字符字符串。 `_wtmpnam` 是 `tmpnam` 的宽字符版本；`_wtmpnam` 的参数和返回值都是宽字符字符串。 `_wtmpnam` 和 `tmpnam` 的行为方式相同，只不过 `_wtmpnam` 不处理多字节字符字符串。  
  
 如果定义了 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC`，则通过调用 [_tempnam_dbg 和 _wtempnam_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) 替换 `_tempnam` 和 `_wtempnam`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_tempnam`|\<stdio.h>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h> 或 \<wchar.h>|  
|`tmpnam`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
```Output  
\s1gk. is safe to use as a temporary file.  
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)
