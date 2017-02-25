---
title: "_snscanf、_snscanf_l、_snwscanf、_snwscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_snwscanf"
  - "_snscanf_l"
  - "_snscanf"
  - "_snwscanf_l"
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
  - "_snscanf"
  - "_snscanf_l"
  - "_snwscanf"
  - "snscanf_l"
  - "snscanf"
  - "_sntscanf_l"
  - "_sntscanf"
  - "_snwscanf_l"
  - "sntscanf_l"
  - "sntscanf"
  - "snwscanf"
  - "snwscanf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_snscanf 函数"
  - "_snscanf_l 函数"
  - "_sntscanf 函数"
  - "_sntscanf_l 函数"
  - "_snwscanf 函数"
  - "_snwscanf_l 函数"
  - "读取数据, 字符串"
  - "snscanf 函数"
  - "snscanf_l 函数"
  - "sntscanf 函数"
  - "sntscanf_l 函数"
  - "snwscanf 函数"
  - "snwscanf_l 函数"
  - "字符串 [C++], 读取"
  - "字符串 [C++], 读取数据自"
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _snscanf、_snscanf_l、_snwscanf、_snwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从字符串中读取一个指定长度的格式化数据。  提供这些函数的更多安全版本；请参见 [\_snscanf\_s、\_snscanf\_s\_l、\_snwscanf\_s、\_snwscanf\_s\_l](../../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)。  
  
## 语法  
  
```  
int __cdecl _snscanf(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   ...  
);  
```  
  
#### 参数  
 `input`  
 检查输入字符串。  
  
 `length`  
 检查在 `input` 中的字符数。  
  
 `format`  
 一个或多个格式说明符。  
  
 `... (optional)`  
 变量通常是指通过在 `format` 的格式说明符存储从输入字符串抽取的值。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 所有这些函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达字符串的末尾，则返回值是 `EOF`。  有关更多信息，请参见[sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 如果 `input` 或 `format` 是一个 `NULL` 指针, 或 `length` 小于等于0, the invalid parameter handler is invoked, 将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 此函数类似于 `sscanf`，除了它可以提供能力从输入字符指定检查的固定字符数。  有关更多信息，请参见[sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_sntscanf`|`_snscanf`|`_snscanf`|`_snwscanf`|  
|`_sntscanf_l`|`_snscanf_l`|`_snscanf_l`|`_snwscanf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_snscanf`, `_snscanf_l`|\<stdio.h\>|  
|`_snwscanf`, `_snwscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_snscanf.c  
// compile with: /W3  
  
#include <stdio.h>  
int main( )  
{  
   char  str1[] = "15 12 14...";  
   wchar_t  str2[] = L"15 12 14...";  
   char  s1[3];  
   wchar_t  s2[3];  
   int   i;  
   float fp;  
  
   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996  
   // Note: _snscanf is deprecated; consider using _snscanf_s instead  
   printf("_snscanf converted %d fields: ", i);  
   printf("%s and %f\n", s1, fp);  
  
   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996  
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead  
   wprintf(L"_snwscanf converted %d fields: ", i);  
   wprintf(L"%s and %f\n", s2, fp);  
}  
```  
  
  **\_snscanf 2 转换字段：15 和 12.000000**  
**\_snwscanf 转换 2 字段：15 和 12.000000**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)