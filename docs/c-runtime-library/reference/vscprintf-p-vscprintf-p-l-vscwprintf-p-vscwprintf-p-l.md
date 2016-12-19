---
title: "_vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l | Microsoft Docs"
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
  - "_vscprintf_p_l"
  - "_vscprintf_p"
  - "_vscwprintf_p_l"
  - "_vscwprintf_p"
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
  - "_vscprintf_p"
  - "_vscprintf_p_l"
  - "vscwprintf_p"
  - "vscprintf_p"
  - "vscwprintf_p_l"
  - "_vscwprintf_p_l"
  - "vscprintf_p_l"
  - "_vscwprintf_p"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vscprintf_p 函数"
  - "_vscprintf_p_l 函数"
  - "_vsctprintf_p 函数"
  - "_vsctprintf_p_l 函数"
  - "_vscwprintf_p 函数"
  - "_vscwprintf_p_l 函数"
  - "vscprintf_p 函数"
  - "vscprintf_p_l 函数"
  - "vsctprintf_p 函数"
  - "vsctprintf_p_l 函数"
  - "vscwprintf_p 函数"
  - "vscwprintf_p_l 函数"
ms.assetid: 5da920b3-8652-4ee9-b19e-5aac3ace9d03
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回字符在格式化字符串中使用一个指向参数列表的数字，并可以指定在已使用参数中的顺序。  
  
## 语法  
  
```  
int _vscprintf_p(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_p _l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf_p (  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_p _l(  
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
 `_vscprintf_p` 返回产生的字符数，如果该字符串所指向的使用指定的格式代码被打印或发送到一个文件或缓冲区的参数列表。  返回的值不包括终止空字符。  `_vscwprintf_p` 为宽字符实现相同的函数。  
  
## 备注  
 这些函数与 `_vscprintf` 和 `_vscwprintf` 唯一不同之处在于它们支持能够指定参数的排序。  有关详细信息，请参阅[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 如果 `format` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
> [!IMPORTANT]
>  请确保，如果 `format` 是用户定义的字符串，则它是终止 null 并具有正确的参数数量和类型。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsctprintf_p`|`_vscprintf_p`|`_vscprintf_p`|`_vscwprintf_p`|  
|`_vsctprintf_p_l`|`_vscprintf_p_l`|`_vscprintf_p_l`|`_vscwprintf_p_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_vscprintf_p`, `_vscprintf_p_l`|\<stdio.h\>|  
|`_vscwprintf_p`, `_vscwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 有关示例，请参阅 [vsprintf](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)。  
  
## 请参阅  
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [\_scprintf\_p、\_scprintf\_p\_l、\_scwprintf\_p、\_scwprintf\_p\_l](../../c-runtime-library/reference/scprintf-p-scprintf-p-l-scwprintf-p-scwprintf-p-l.md)   
 [\_vscprintf、\_vscprintf\_l、\_vscwprintf、\_vscwprintf\_l](../../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)