---
title: "_mktemp、_wmktemp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
dev_langs:
- C++
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
caps.latest.revision: 25
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: b6b5f2f059084e1f5dd66d75b5f5af5f2ade2473
ms.lasthandoff: 02/24/2017

---
# <a name="mktemp-wmktemp"></a>_mktemp、_wmktemp
创建唯一的文件名。 提供这些函数的更多安全版本，请参阅 [_mktemp_s、_wmktemp_s](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `template`  
 文件名模式。  
  
## <a name="return-value"></a>返回值  
 这些函数各返回一个指向已修改模板的指针。 如果 `NULL` 格式有误或者没有更多从给定模板创建的唯一名称，函数将返回 `template`。  
  
## <a name="remarks"></a>备注  
 `_mktemp` 函数通过修改 `template` 参数创建唯一的文件名。 `_mktemp` 根据需要自动处理多字节字符字符串参数，并根据运行时系统根据当前使用的多字节代码页识别多字节字符序列。 `_wmktemp` 是 `_mktemp` 的宽字符版本；`_wmktemp` 的参数和返回值都是宽字符字符串。 `_wmktemp` 和 `_mktemp` 的行为方式相同，只不过 `_wmktemp` 不处理多字节字符字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 `template` 参数的形式为 `base`XXXXXX，其中 `base` 是您提供的新文件名的部分，而每个 X 是 `_mktemp` 提供的字符的占位符。 `template` 中的每个占位符字符必须为大写 X。`_mktemp` 保留 `base`，并使用字母字符替换第一个尾随的 X。 `_mktemp` 会将后面的尾随 X 替换为五位数值；此值是标识调用进程（在多线程程序中则为调用线程）的唯一数字。  
  
 每次成功调用 `_mktemp` 都将修改 `template`。 在来自具有相同的 `template` 参数的相同进程或线程的每个后续调用中，`_mktemp` 将检查与以前的调用中的 `_mktemp` 返回的名称匹配的文件名。 如果给定名称的文件不存在，`_mktemp` 将返回该名称。 如果之前返回的所有名称的文件都存在，`_mktemp` 会通过将之前返回的名称中使用的字母字符替换为下一个可用小写字母（按从“a”到“z”的顺序）来创建新名称。 例如，如果 `base` 为：  
  
```  
fn  
```  
  
 并且 `_mktemp` 提供的五位数值为 12345，则返回的第一个名称为：  
  
```  
fna12345  
```  
  
 如果此名称用于创建文件 FNA12345 并且此文件仍存在，则来自具有相同的 `base`（适用于 `template`）的相同进程或线程的调用返回的下一个名称为：  
  
```  
fnb12345  
```  
  
 如果 FNA12345 不存在，则返回的下一个名称又是：  
  
```  
fna12345  
```  
  
 `_mktemp` 可以为基值和模板值的任意给定组合创建最多 26 个唯一文件名。 因此，FNZ12345 是 `_mktemp` 可为本示例中使用的 `base` 和 `template` 值创建的最后一个唯一文件名。  
  
 如果失败，则会设置 `errno`。 如果 `template` 具有无效的格式（例如，少于 6 个 X），`errno` 将设置为 `EINVAL`。 如果 `_mktemp` 因为所有 26 个可能的文件名都已存在而无法创建唯一名称，`_mktemp` 会将模板设置为空字符串并返回 `EEXIST`。  
  
 在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mktemp`|\<io.h>|  
|`_wmktemp`|\<io.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_mktemp.c  
// compile with: /W3  
/* The program uses _mktemp to create  
 * unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
#include <errno.h>  
  
char *template = "fnXXXXXX";  
char *result;  
char names[27][9];  
  
int main( void )  
{  
   int i;  
   FILE *fp;  
  
   for( i = 0; i < 27; i++ )  
   {  
      strcpy_s( names[i], sizeof( names[i] ), template );  
      /* Attempt to find a unique filename: */  
      result = _mktemp( names[i] );  // C4996  
      // Note: _mktemp is deprecated; consider using _mktemp_s instead  
      if( result == NULL )  
      {  
         printf( "Problem creating the template\n" );  
         if (errno == EINVAL)  
         {  
             printf( "Bad parameter\n");  
         }  
         else if (errno == EEXIST)  
         {  
             printf( "Out of unique filenames\n");   
         }  
      }  
      else  
      {  
         fopen_s( &fp, result, "w" );  
         if( fp != NULL )  
            printf( "Unique filename is %s\n", result );  
         else  
            printf( "Cannot open %s\n", result );  
         fclose( fp );  
      }  
   }  
}  
```  
  
```Output  
Unique filename is fna03912  
Unique filename is fnb03912  
Unique filename is fnc03912  
Unique filename is fnd03912  
Unique filename is fne03912  
Unique filename is fnf03912  
Unique filename is fng03912  
Unique filename is fnh03912  
Unique filename is fni03912  
Unique filename is fnj03912  
Unique filename is fnk03912  
Unique filename is fnl03912  
Unique filename is fnm03912  
Unique filename is fnn03912  
Unique filename is fno03912  
Unique filename is fnp03912  
Unique filename is fnq03912  
Unique filename is fnr03912  
Unique filename is fns03912  
Unique filename is fnt03912  
Unique filename is fnu03912  
Unique filename is fnv03912  
Unique filename is fnw03912  
Unique filename is fnx03912  
Unique filename is fny03912  
Unique filename is fnz03912  
Problem creating the template.  
Out of unique filenames.  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)
