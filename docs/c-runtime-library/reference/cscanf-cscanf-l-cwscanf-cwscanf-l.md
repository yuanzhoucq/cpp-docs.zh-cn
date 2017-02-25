---
title: "_cscanf、_cscanf_l、_cwscanf、_cwscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cscanf_l"
  - "_cscanf"
  - "_cwscanf"
  - "_cwscanf_l"
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
  - "_cwscanf"
  - "cwscanf_l"
  - "tcscanf_l"
  - "_tcscanf_l"
  - "_cscanf"
  - "_cscanf_l"
  - "tcscanf"
  - "cwscanf"
  - "_cwscanf_l"
  - "cscanf_l"
  - "_tcscanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cscanf 函数"
  - "_cscanf_l 函数"
  - "_cwscanf 函数"
  - "_cwscanf_l 函数"
  - "_tcscanf 函数"
  - "_tcscanf_l 函数"
  - "cscanf_l 函数"
  - "cwscanf 函数"
  - "cwscanf_l 函数"
  - "数据 [C++], 从控制台读取"
  - "读取数据 [C++], 从控制台中"
  - "tcscanf 函数"
  - "tcscanf_l 函数"
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _cscanf、_cscanf_l、_cwscanf、_cwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从控制台读取格式数据。  有关这些函数的更多安全版本，请参见 [\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _cscanf(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_l(   
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
 成功转换并分配字段数。  返回值不包括读取，但未赋值的字段。  返回值是`EOF` ，它尝试在文件末尾读取。  当键入被重定向的操作系统命令行级别时，该情况可能发生。  返回值为 0 表示未分配字段。  
  
## 备注  
 `_cscanf` 函数直接从控制台读取数据到由`argument`给定的位置。  [\_getche](../../c-runtime-library/reference/getch-getwch.md) 函数用于读取字符。  每个任意参数必须是指向类型变量的指针，此类型需与 `format` 中的类型说明符对应。  这种格式控制输入字段的解释，并且形式和函数都与 [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数的`format` 参数相同。  `_cscanf` 正常回显输入字符，如果最后是对 `_ungetch`的调用，则不这样。  
  
 此函数验证其参数。  如果format为 NULL，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述 。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`EOF`。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscanf`|`_cscanf`|`_cscanf`|`_cwscanf`|  
|`_tcscanf_l`|`_cscanf_l`|`_cscanf_l`|`_cwscanf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cscanf`,`_cscanf_l`|\<conio.h\>|  
|`_cwscanf`, `_cwscanf_l`|\<conio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_cscanf.c  
// compile with: /c /W3  
/* This program prompts for a string  
 * and uses _cscanf to read in the response.  
 * Then _cscanf returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int   result, i[3];  
  
   _cprintf_s( "Enter three integers: ");  
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996  
   // Note: _cscanf is deprecated; consider using _cscanf_s instead  
   _cprintf_s( "\r\nYou entered " );  
   while( result-- )  
      _cprintf_s( "%i ", i[result] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## 输入  
  
```  
1 2 3  
```  
  
## Output  
  
```  
Enter three integers: 1 2 3  
You entered 3 2 1  
```  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)