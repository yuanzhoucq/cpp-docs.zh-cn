---
title: "_scprintf_p、_scprintf_p_l、_scwprintf_p、_scwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_scwprintf_p"
  - "_scprintf_p_l"
  - "_scwprintf_p_l"
  - "_scprintf_p"
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
  - "_scwprintf_p_l"
  - "_sctprintf_p"
  - "scprintf_p_l"
  - "scprintf_p"
  - "_sctprintf_p_l"
  - "scwprintf_p"
  - "_scprintf_p_l"
  - "scwprintf_p_l"
  - "_scprintf_p"
  - "_scwprintf_p"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_scprintf_p 函数"
  - "_scprintf_p_l 函数"
  - "_sctprintf_p 函数"
  - "_sctprintf_p_l 函数"
  - "_scwprintf_p 函数"
  - "_scwprintf_p_l 函数"
  - "scprintf_p 函数"
  - "scprintf_p_l 函数"
  - "sctprintf_p 函数"
  - "sctprintf_p_l 函数"
  - "scwprintf_p 函数"
  - "scwprintf_p_l 函数"
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _scprintf_p、_scprintf_p_l、_scwprintf_p、_scwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回格式化字符串中字符的数量，能够指定参数在格式字符串的顺序。  
  
## 语法  
  
```  
int _scprintf_p(  
   const char *format [,  
   argument] ...   
);  
int _scprintf_p_l(  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _scwprintf_p (  
   const wchar_t *format [,  
   argument] ...   
);  
int _scwprintf_p _l(  
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
  
## 返回值  
 返回使用指定的格式代码生成字符数，如果字符串将打印或发送到文件或缓冲区。  返回的值不包括终止空字符。  `_scwprintf_p` 为宽字符实现相同的函数。  
  
 在 `_scprintf_p` 和 `_scprintf` 的不同之处在于 `_scprintf_p` 支持位置参数，允许指定排序参数用于格式字符串。  有关详细信息，请参阅[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
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
|`_sctprintf_p`|`_scprintf_p`|`_scprintf_p`|`_scwprintf_p`|  
|`_sctprintf_p_l`|`_scprintf_p_l`|`_scprintf_p_l`|`_scwprintf_p_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_scprintf_p`, `_scprintf_p_l`|\<stdio.h\>|  
|`_scwprintf_p`, `_scwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_scprintf、\_scprintf\_l、\_scwprintf、\_scwprintf\_l](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)