---
title: "_configthreadlocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_configthreadlocale"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_configthreadlocale"
  - "configthreadlocale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_configthreadlocale 函数"
  - "configthreadlocale 函数"
  - "区域设置, 每线程"
  - "每线程区域设置"
  - "线程区域设置"
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _configthreadlocale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配置每个线程区域设置选项。  
  
## 语法  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
#### 参数  
 `type`  
 要设置的选项。  选项中的一个列在下面的表中。  
  
## 返回值  
 上述每个线程区域设置状态 \(`_DISABLE_PER_THREAD_LOCALE` 或 `_ENABLE_PER_THREAD_LOCALE`\)，或者失败时为\-1。  
  
## 备注  
 `_configurethreadlocale` 函数用于控制使用线程的特定区域设置。  使用以下选项之一指定或确定每个线程区域设置状态：  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 使当前线程使用线程特定区域设置。  线程随后调用 `setlocale` 只影响线程自己的区域设置。  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 使当前线程使用全局区域设置。  使用全局区域设置，线程后续调用 `setlocale` 影响其他线程。  
  
 `0`  
 为特定的线程检索当前设置。  
  
 这些功能会影响 `setlocale`、`_tsetlocale`、`_wsetlocale`、`_beginthread`和 `_beginthreadex`的行为。  如果另一个方法用于创建线程，区域设置对这些线程没有影响。  
  
 在每个线程区域设置禁用时，任何后续调用 `setlocale` 或 `_wsetlocale` 更改所有线程区域设置。  在每个线程区域设置启用时，`setlocale` 或 `_wsetlocale` 仅影响当前线程的区域设置。  
  
 如果使用 `_configurethreadlocale` 启用每个线程区域设置，我们建议您调用 `setlocale` 或 `_wsetlocale` 设置该线程的首选区域设置。  
  
 如果 `type` 不是在表中列出的某个值，此函数调用的无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果继续执行，这个函数设置`errno`为`EINVAL` 并返回\-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_configthreadlocale`|\<locale.h\>|  
  
## 示例  
  
```  
// crt_configthreadlocale.cpp  
//   
// This program demonstrates the use of _configthreadlocale when  
// using is two independent threads.  
//  
  
#include <locale.h>  
#include <process.h>  
#include <windows.h>  
#include <stdio.h>  
#include <time.h>  
  
#define BUFF_SIZE 100  
  
// Retrieve the date and time in the current  
// locale's format.  
int get_time(unsigned char* str)  
{  
    __time64_t  ltime;  
    struct tm   thetime;  
  
    // Retieve the time  
    _time64(&ltime);  
    _gmtime64_s(&thetime, &ltime);  
  
    // Format the current time structure into a string  
    // using %#x is the long date representation,  
    // appropriate to the current locale  
    if (!strftime((char *)str, BUFF_SIZE, "%#x",   
                  (const struct tm*)&thetime))  
    {  
        printf("strftime failed!\n");  
        return -1;  
    }  
    return 0;  
}  
  
// This thread sets its locale to German  
// and prints the time.  
unsigned __stdcall SecondThreadFunc( void* pArguments )  
{  
    unsigned char str[BUFF_SIZE];  
  
    // Set the thread code page  
    _setmbcp(_MB_CP_ANSI)  
  
    // Set the thread locale  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "German"));  
  
    // Retrieve the time string from the helper function  
    if (get_time(str) == 0)  
    {  
        printf("The time in German locale is: '%s'\n", str);  
    }  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
// The main thread spawns a second thread (above) and then  
// sets the locale to English and prints the time.  
int main()  
{   
    HANDLE          hThread;  
    unsigned        threadID;  
    unsigned char   str[BUFF_SIZE];  
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
  
    // Retrieve the time string from the helper function  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "English"));  
  
    // Create the second thread.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,  
                                      NULL, 0, &threadID );  
  
    if (get_time(str) == 0)  
    {  
        // Retrieve the time string from the helper function  
        printf("The time in English locale is: '%s'\n\n", str);  
    }  
  
    // Wait for the created thread to finish.  
    WaitForSingleObject( hThread, INFINITE );  
  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
  **线程区域设置现在设置为 English\_United States.1252。**  
**在英国区域设置中时间为：'Wednesday, May 12, 2004'**  
**线程区域设置现在设置为 German\_Germany.1252。**  
**在德国区域设置中时间为：“Mittwoch，12。  Mai 2004 "**    
## .NET Framework 等效项  
 不适用。但是，请参见 [使用 CurrentCulture 属性](http://msdn.microsoft.com/zh-cn/3156042d-6082-4205-90b4-c917ae6a3ba6)。  
  
## 请参阅  
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多线程和区域设置](../../parallel/multithreading-and-locales.md)