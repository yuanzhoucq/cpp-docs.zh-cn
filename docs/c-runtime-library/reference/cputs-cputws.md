---
title: "_cputs、_cputws | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cputws"
  - "_cputs"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "cputws"
  - "_cputs"
  - "_cputws"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cputs 函数"
  - "_cputws 函数"
  - "控制台, 发送字符串到"
  - "cputs 函数"
  - "cputws 函数"
  - "将字符串放置到控制台"
  - "字符串 [C++], 写入"
ms.assetid: ec418484-0f8d-43ec-8d8b-198a556c659e
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cputs、_cputws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串放到控制台。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
  
        int _cputs(   
const char *str   
);  
int _cputws(  
const wchar_t *str   
);  
```  
  
#### 参数  
 `str`  
 输出字符串。  
  
## 返回值  
 如果成功，则 `_cputs` 返回 0。  如果函数失败，则返回非零值。  
  
## 备注  
 `_cputs` 函数将由 `str` 指向的以 null 终止的字符串直接写入控制台。  回车换行符 \(CR\-LF\) 组合不会自动追加到字符串。  
  
 此函数验证其参数。  如果 `str` 为 **NULL**，则会调用无效的函数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则 `errno` 设置为 `EINVAL` 并返回 \-1。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_cputts**|`_cputs`|`_cputs`|`_cputws`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_cputs`|\<conio.h\>|\<errno.h\>|  
|`_cputws`|\<conio.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_cputs.c  
// compile with: /c  
// This program first displays a string to the console.  
  
#include <conio.h>  
#include <errno.h>  
  
void print_to_console(char* buffer)  
{  
   int retval;  
   retval = _cputs( buffer );  
   if (retval)  
   {  
       if (errno == EINVAL)  
       {  
         _cputs( "Invalid buffer in print_to_console.\r\n");  
       }  
       else  
         _cputs( "Unexpected error in print_to_console.\r\n");  
   }  
}  
  
void wprint_to_console(wchar_t* wbuffer)  
{  
   int retval;  
   retval = _cputws( wbuffer );  
   if (retval)  
   {  
       if (errno == EINVAL)  
       {  
         _cputws( L"Invalid buffer in wprint_to_console.\r\n");  
       }  
       else  
         _cputws( L"Unexpected error in wprint_to_console.\r\n");  
   }  
}  
  
int main()  
{  
  
   // String to print at console.   
   // Notice the \r (return) character.   
   char* buffer = "Hello world (courtesy of _cputs)!\r\n";  
   wchar_t *wbuffer = L"Hello world (courtesy of _cputws)!\r\n";  
   print_to_console(buffer);  
   wprint_to_console( wbuffer );  
}  
```  
  
## 输出  
  
```  
Hello world (courtesy of _cputs)!  
Hello world (courtesy of _cputws)!  
```  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_putch、\_putwch](../../c-runtime-library/reference/putch-putwch.md)