---
title: "_mktemp_s、_wmktemp_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mktemp_s
- _wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1289db9b04b9636680439980046fc9532181bd13
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="mktemps-wmktemps"></a>_mktemp_s、_wmktemp_s
创建唯一的文件名。 如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些版本的 [_mktemp、_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) 具有安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `template`  
 文件名模式。  
  
 `sizeInChars`  
 `_mktemp_s` 中单字节字符的缓冲区大小；`_wmktemp_s` 中的宽字符，包括空终止符。  
  
## <a name="return-value"></a>返回值  
 如果成功，这两个函数返回零；如果失败，则返回错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`template`|`sizeInChars`|**返回值**|**模板中的新值**|  
|----------------|-------------------|----------------------|-------------------------------|  
|`NULL`|任何|`EINVAL`|`NULL`|  
|格式不正确（请参阅`Remarks`部分查看正确格式）|任何|`EINVAL`|空字符串|  
|任何|<= X 的数量|`EINVAL`|空字符串|  
  
 如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且函数将返回 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_mktemp_s` 函数通过修改 `template` 参数创建唯一的文件名，以便在调用后，`template` 指针指向包含新文件名的字符串。 `_mktemp_s` 根据需要自动处理多字节字符字符串参数，并根据运行时系统根据当前使用的多字节代码页识别多字节字符序列。 `_wmktemp_s` 是 `_mktemp_s` 的宽字符版本；`_wmktemp_s` 的参数是宽字符字符串。 `_wmktemp_s` 和 `_mktemp_s` 的行为方式相同，只不过 `_wmktemp_s` 不处理多字节字符字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 `template` 自变量的形式为 `baseXXXXXX`，其中 `base` 是你提供的新文件名的部分，而每个 X 是 `_mktemp_s` 提供的字符的占位符。 `template` 中的每个占位符字符必须为大写 X。`_mktemp_s` 保留 `base`，并使用字母字符替换第一个尾随的 X。 `_mktemp_s` 会将后面的尾随 X 替换为五位数值；此值是标识调用进程（在多线程程序中则为调用线程）的唯一数字。  
  
 每次成功调用 `_mktemp_s` 都将修改 `template`。 在来自具有相同的 `template` 参数的相同进程或线程的每个后续调用中，`_mktemp_s` 将检查与以前的调用中的 `_mktemp_s` 返回的名称匹配的文件名。 如果给定名称的文件不存在，`_mktemp_s` 将返回该名称。 如果之前返回的所有名称的文件都存在，`_mktemp_s` 会通过将之前返回的名称中使用的字母字符替换为下一个可用小写字母（按从“a”到“z”的顺序）来创建新名称。 例如，如果 `base` 为：  
  
```  
fn  
```  
  
 并且 `_mktemp_s` 提供的五位数值为 12345，则返回的第一个名称为：  
  
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
  
 `_mktemp_s` 可以为基值和模板值的任意给定组合创建最多 26 个唯一文件名。 因此，FNZ12345 是 `_mktemp_s` 可为本示例中使用的 `base` 和 `template` 值创建的最后一个唯一文件名。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_mktemp_s`|\<io.h>|  
|`_wmktemp_s`|\<io.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)