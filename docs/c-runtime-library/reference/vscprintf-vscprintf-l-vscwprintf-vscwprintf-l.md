---
title: "_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vscprintf"
  - "_vscprintf_l"
  - "_vscwprintf_l"
  - "_vscwprintf"
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
  - "vscprintf_l"
  - "vscwpeintf"
  - "_vscwprintf"
  - "_vsctprintf"
  - "_vscprintf"
  - "vscwprintf_l"
  - "vscprintf"
  - "_vscwprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vscprintf 函数"
  - "_vscprintf_l 函数"
  - "_vsctprintf 函数"
  - "_vsctprintf_l 函数"
  - "_vscwprintf 函数"
  - "_vscwprintf_l 函数"
  - "格式化文本 [C++]"
  - "vscprintf 函数"
  - "vscprintf_l 函数"
  - "vsctprintf 函数"
  - "vsctprintf_l 函数"
  - "vscwprintf 函数"
  - "vscwprintf_l 函数"
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回的字符数量的格式字符串中使用指针到参数列表。  
  
## 语法  
  
```  
int _vscprintf(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 参数  
 `format`  
 窗体控件字符串。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 `_vscprintf` 返回产生的字符数，如果该字符串所指向的使用指定的格式代码被打印或发送到一个文件或缓冲区的参数列表。  返回的值不包括终止空字符。  `_vscwprintf` 为宽字符实现相同的函数。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 如果 `format` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
## 备注  
 每个 `argument`（如果有）根据 `format` 中相应的格式规范进行转换。  该格式包括普通字符，其形式和函数与 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 `format` 参数相同。  
  
> [!IMPORTANT]
>  请确保，如果 `format` 是用户定义的字符串，则它是终止 null 并具有正确的参数数量和类型。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE &\_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsctprintf`|`_vscprintf`|`_vscprintf`|`_vscwprintf`|  
|`_vsctprintf_l`|`_vscprintf_l`|`_vscprintf_l`|`_vscwprintf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_vscprintf`, `_vscprintf_l`|\<stdio.h\>|  
|`_vscwprintf`, `_vscwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 有关示例，请参阅 [vsprintf](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)