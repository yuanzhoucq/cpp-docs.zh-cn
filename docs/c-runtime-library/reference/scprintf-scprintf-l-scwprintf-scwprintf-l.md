---
title: "_scprintf、_scprintf_l、_scwprintf、_scwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_scprintf_l"
  - "_scwprintf"
  - "_scwprintf_l"
  - "_scprintf"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "scprintf"
  - "_scprintf_l"
  - "_scwprintf_l"
  - "_scprintf"
  - "scwprintf"
  - "_scwprintf"
  - "scprintf_l"
  - "_sctprintf_l"
  - "scwprintf_l"
  - "_sctprintf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_scprintf 函数"
  - "_scprintf_l 函数"
  - "_sctprintf 函数"
  - "_sctprintf_l 函数"
  - "_scwprintf 函数"
  - "_scwprintf_l 函数"
  - "格式化文本 [C++]"
  - "scprintf 函数"
  - "scprintf_l 函数"
  - "sctprintf 函数"
  - "sctprintf_l 函数"
  - "scwprintf 函数"
  - "scwprintf_l 函数"
ms.assetid: ecbb0ba6-5f4c-4ce6-a64b-144ad8b5fe92
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _scprintf、_scprintf_l、_scwprintf、_scwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回 formatted string 中的字符数。  
  
## 语法  
  
```  
int _scprintf(  
   const char *format [,  
   argument] ...   
);  
int _scprintf_l(  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _scwprintf(  
   const wchar_t *format [,  
   argument] ...   
);  
int _scwprintf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
```  
  
#### 参数  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 返回使用指定的格式代码生成字符数，如果字符串将打印或发送到文件或缓冲区。  返回的值不包括终止空字符。  `_scwprintf` 为宽字符实现相同的函数。  
  
 如果 `format` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个 `argument`（如果有）根据 `format` 中相应的格式规范进行转换。  该格式包括普通字符，其形式和函数与 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 `format` 参数相同。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_sctprintf`|`_scprintf`|`_scprintf`|`_scwprintf`|  
|`_sctprintf_l`|`_scprintf_l`|`_scprintf_l`|`_scwprintf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_scprintf`, `_scprintf_l`|\<stdio.h\>|  
|`_scwprintf`, `_scwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt__scprintf.c  
  
#define _USE_MATH_DEFINES  
  
#include <stdio.h>  
#include <math.h>  
#include <malloc.h>  
  
int main( void )  
{  
   int count;  
   int size;  
   char *s = NULL;  
  
   count = _scprintf( "The value of Pi is calculated to be %f.\n",  
                      M_PI);  
  
   size = count + 1; // the string will need one more char for the null terminator  
   s = malloc(sizeof(char) * size);  
   sprintf_s(s, size, "The value of Pi is calculated to be %f.\n",  
                      M_PI);  
   printf("The length of the following string will be %i.\n", count);  
   printf("%s", s);  
   free( s );  
}  
```  
  
  **如下字符串长度为46**  
**值 Pi 计算为 3.141593。**   
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)