---
title: "_getche、_getwche | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getwche
- _getche
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
- getwche
- _getche
- _getwche
dev_langs: C++
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19c80094cb613900ce8ffb2713b8e94a5826def4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="getche-getwche"></a>_getche、_getwche
从具有回显的控制台获取字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _getche( void );  
wint_t _getwche( void );  
```  
  
## <a name="return-value"></a>返回值  
 返回读取的字符。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `_getche` 和 `_getwche` 函数从具有回显的控制台读取单个字符，这意味着，字符会在控制台中显示。 无可用于读取 CTRL+C 的函数。 在读取功能键或箭头键时，必须调用每个函数两次；第一次调用返回 0 或 0xE0，并且第二个调用会返回实际的键代码。  
  
 这些函数会锁定调用线程，因此是线程安全的。 有关非锁定版本的信息，请参阅 [_getche_nolock、_getwche_nolock](../../c-runtime-library/reference/getche-nolock-getwche-nolock.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_getche`|`_getche`|`_getch`|`_getwche`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_getche`|\<conio.h>|  
|`_getwche`|\<conio.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_getche.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getche();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed       
}  
```  
  
```Input  
abcdefy
```
  
```Output  
Type 'Y' when finished typing keys: abcdefyY  
```  
  
## <a name="see-also"></a>请参阅  
 [控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_cgets、_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)