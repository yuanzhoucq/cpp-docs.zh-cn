---
title: "gets_s、_getws_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getws_s
- gets_s
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
- _getws_s
- gets_s
dev_langs:
- C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 4f4a10f432c663be33fe751bcde862c4d8e57c49
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="getss-getwss"></a>gets_s、_getws_s
从 `stdin` 流中获取行。 这些版本的 [gets、_getws](../../c-runtime-library/gets-getws.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 输入字符串的存储位置。  
  
 [in] `sizeInCharacters`  
 缓冲区的大小。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `buffer`。 `NULL` 指针指示错误或文件尾条件。 使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 确定已发生哪种情况。  
  
## <a name="remarks"></a>备注  
 `gets_s` 函数从标准输入流 `stdin` 中读取一个行并将该行存储在 `buffer` 中。 该行由第一个换行符(“\n”)之前的所有字符和该换行符构成。 随后，在返回行之前，`gets_s` 会将换行符替换为 null 字符（“\0”）。 相反，`fgets_s` 函数将保留换行符。  
  
 如果读取的第一个字符是文件尾字符，则空字符将存储在 `buffer` 的开头，并返回 `NULL`。  
  
 `_getws` 是 `gets_s` 的宽字符版本；其参数和返回值都是宽字符字符串。  
  
 如果 `buffer` 为 `NULL` 或 `sizeInCharacters` 小于或等于零，或者如果缓冲区太小，无法包含输入行和 null 终止符，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `NULL` 并将 errno 设置为 `ERANGE`。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`gets_s`|\<stdio.h>|  
|`_getws`|\<stdio.h> 或 \<wchar.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [gets、_getws](../../c-runtime-library/gets-getws.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [puts、_putws](../../c-runtime-library/reference/puts-putws.md)
