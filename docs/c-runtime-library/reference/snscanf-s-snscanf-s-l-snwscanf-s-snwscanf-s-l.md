---
title: "_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_snwscanf_s_l"
  - "_snwscanf_s"
  - "_snscanf_s"
  - "_snscanf_s_l"
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
  - "_sntscanf_s"
  - "snscanf_s"
  - "_snwscanf_s_l"
  - "sntscanf_s_l"
  - "snwscanf_s_l"
  - "snwscanf_s"
  - "_snscanf_s"
  - "_snwscanf_s"
  - "snscanf_s_l"
  - "_sntscanf_s_l"
  - "_snscanf_s_l"
  - "sntscanf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_snscanf_s 函数"
  - "_snscanf_s_l 函数"
  - "_sntscanf_s 函数"
  - "_sntscanf_s_l 函数"
  - "_snwscanf_s 函数"
  - "_snwscanf_s_l 函数"
  - "读取数据, 字符串"
  - "snscanf_s 函数"
  - "snscanf_s_l 函数"
  - "sntscanf_s 函数"
  - "sntscanf_s_l 函数"
  - "snwscanf_s 函数"
  - "snwscanf_s_l 函数"
  - "字符串 [C++], 读取"
  - "字符串 [C++], 读取数据自"
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从字符串中读取一个指定长度的格式化数据。  [\_snscanf、\_snscanf\_l、\_snwscanf、\_snwscanf\_l](../../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
int __cdecl _snscanf_s(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_s_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf_s(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_s_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   …  
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
 所有这些函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达字符串的末尾，则返回值是 `EOF`。  有关详细信息，请参阅[sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
 如果 `input` 或 `format` 是 `NULL` 指针，无效参数处理器程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 此函数类似于 `sscanf_s`，除了它可以提供能力从输入字符指定检查的固定字符数。  有关详细信息，请参阅[sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
 缓冲区大小参数需要具有类型字段字符 `c`、`C`、`s`、`S`和 `[`。  有关详细信息，请参阅[scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小参数的类型为 `unsigned` 而非 `size_t`。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_sntscanf_s`|`_snscanf_s`|`_snscanf_s`|`_snwscanf_s`|  
|`_sntscanf_s_l`|`_snscanf_s_l`|`_snscanf_s_l`|`_snwscanf_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_snscanf_s`, \_`snscanf_s_l`|\<stdio.h\>|  
|`_snwscanf_s`, `_snwscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_snscanf_s.c  
// This example scans a string of   
// numbers, using both the character  
// and wide character secure versions  
// of the snscanf function.  
  
#include <stdio.h>  
  
int main( )  
{  
    char        str1[] = "15 12 14...";  
    wchar_t     str2[] = L"15 12 14...";  
    char        s1[3];  
    wchar_t     s2[3];  
    int         i;  
    float       fp;  
  
    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);  
    printf_s("_snscanf_s converted %d fields: ", i);  
    printf_s("%s and %f\n", s1, fp);  
  
    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);  
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);  
    wprintf_s(L"%s and %f\n", s2, fp);  
}  
```  
  
  **\_snscanf\_s 2 转换字段：15 和 12.000000**  
**\_snwscanf\_s 转换 2 字段：15 和 12.000000**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)