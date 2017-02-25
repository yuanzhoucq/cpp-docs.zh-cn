---
title: "setlocale、_wsetlocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsetlocale"
  - "setlocale"
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
  - "_wsetlocale"
  - "_tsetlocale"
  - "setlocale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tsetlocale 函数"
  - "_wsetlocale 函数"
  - "定义区域设置"
  - "区域设置, 定义"
  - "setlocale 函数"
  - "tsetlocale 函数"
  - "wsetlocale 函数"
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# setlocale、_wsetlocale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置或检索运行时区域设置。  
  
## 语法  
  
```  
char *setlocale(  
   int category,  
   const char *locale   
);  
wchar_t *_wsetlocale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### 参数  
 `category`  
 受区域设置影响的分类。  
  
 `locale`  
 区域设置说明符。  
  
## 返回值  
 如果提供了有效的 `locale` 和 `category`，则返回指向与指定的 `locale` 和 `category` 关联的字符串的指针。  如果 `locale` 或 `category` 无效，则返回空指针，并且不更改程序的当前区域设置。  
  
 例如，调用  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 设置所有类别，只返回该字符串  
  
 `en-US`  
  
 你可以复制由 `setlocale` 返回的字符串以还原程序的区域设置信息的该部分。  全局或线程本地存储用于由 `setlocale` 返回的字符串。  稍后调用 `setlocale` 将覆盖字符串，这将使之前调用返回的字符串指针无效。  
  
## 备注  
 使用 `setlocale` 函数设置、更改或查询 `locale` 和 `category` 指定的部分或全部当前程序区域设置信息。  `locale` 是指可为其自定义程序的某些方面的局部性（国家\/地区和语言）。  一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。  如果将 `locale` 设置为一种语言的默认字符串（此字符串在你的计算机上具有多个受支持的形式），则应选定 `setlocale` 返回值以查看哪种语言有效。  例如，如果将 `locale` 设置为“chinese”，则返回值可能是“chinese\-simplified”或“chinese\-traditional”。  
  
 `_wsetlocale` 是 `setlocale` 的宽字符版本；`locale` 参数和`_wsetlocale` 的返回值都是宽字符字符串。  除此以外，`_wsetlocale` 和 `setlocale` 的行为完全相同。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|  
  
 `category` 参数指定程序的受影响的部分区域设置信息。  用于 `category` 的宏及其影响的程序的部分如下：  
  
 `LC_ALL`  
 以下列表中的所有类别。  
  
 `LC_COLLATE`  
 `strcoll`、`_stricoll`、`wcscoll`、`_wcsicoll`、`strxfrm`、`_strncoll`、`_strnicoll`、`_wcsncoll`、`_wcsnicoll` 和 `wcsxfrm` 函数。  
  
 `LC_CTYPE`  
 字符处理函数（不受影响的 `isdigit`、`isxdigit`、`mbstowcs` 和 `mbtowc` 除外）。  
  
 `LC_MONETARY`  
 `localeconv` 函数返回的货币格式信息。  
  
 `LC_NUMERIC`  
 格式化输出例程（例如 `printf`）、数据转换例程和 `localeconv` 所返回的非货币格式设置信息的十进制点字符。  除小数点字符之外，`LC_NUMERIC` 还设置 [localeconv](../../c-runtime-library/reference/localeconv.md) 返回的千位分隔符和分组控件字符串。  
  
 `LC_TIME`  
 `strftime` 和 `wcsftime` 函数。  
  
 此函数验证类别参数。  如果类别参数不是上表中提供的值之一，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
 `locale` 参数是指向指定区域设置的字符串的指针。  有关 `locale` 参数的格式的信息，请参阅[区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  如果 `locale` 指向一个空字符串，则区域设置是实现定义的本机环境。  `C` 的值为 C 转换指定最小的符合 ANSI 标准的环境。  `C` 区域设置假设所有 `char` 数据类型为 1 字节，并且其值始终小于 256。  
  
 在程序启动时，将执行以下语句的等效项：  
  
 `setlocale( LC_ALL, "C" );`  
  
 `locale` 参数可以采用区域设置名称、语言字符串、语言字符串和国家\/地区代码、代码页或语言字符串、国家\/地区代码和代码页。  可用区域设置名称、语言、国家\/地区代码和代码页集包含 Windows NLS API 支持的所有内容，要求每个字符对应两个以上的字节的代码页除外（如 UTF\-7 和 UTF\-8）。  如果你提供的代码页值为 UTF\-7 或 UTF\-8，则 `setlocale` 将失败并返回 null。  `setlocale` 支持的区域设置名称集，如[区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中所述。  [语言字符串](../../c-runtime-library/language-strings.md)和[国家\/地区字符串](../../c-runtime-library/country-region-strings.md)中列出了 `setlocale` 支持的语言和国家\/地区字符串集。  建议对嵌入到代码中或序列化到存储中的区域设置字符串的性能和可维护性使用区域设置名称格式。  与语言和国家\/地区名称格式相比，操作系统的更新更改区域设置名称字符串的可能性会小一些。  
  
 作为 `locale` 参数传递的 null 指针告知 `setlocale` 查询而不是设置国际环境。  如果 `locale` 参数为 null 指针，则不更改程序的当前区域设置。  相反，`setlocale` 返回指向字符串的指针，该字符串与线程的当前区域设置的 `category` 关联。  如果 `category` 参数为 `LC_ALL`，则该函数返回一个指示每个类别的当前设置（由分号分隔）的字符串。  例如，调用的顺序  
  
 `// Set all categories and return "en-US"`  
  
 `setlocale(LC_ALL, "en-US");`  
  
 `// Set only the LC_MONETARY category and return "fr-FR"`  
  
 `setlocale(LC_MONETARY, "fr-FR");`  
  
 `printf("%s\n", setlocale(LC_ALL, NULL));`  
  
 返回  
  
 `LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US`  
  
 它是与 `LC_ALL` 类别关联的字符串。  
  
 以下示例与 `LC_ALL` 类别相关。  可使用字符串“.OCP”或“.ACP”而非代码页号来分别指定用户默认的 OEM 代码页和用户默认的 ANSI 代码页的用法。  
  
 `setlocale( LC_ALL, "" );`  
 将区域设置设定为默认值，该值是从操作系统获得的用户默认的 ANSI 代码页。  
  
 `setlocale( LC_ALL, ".OCP" );`  
 将设置区域显式设置为从操作系统获得的当前 OEM 代码页。  
  
 `setlocale( LC_ALL, ".ACP" );`  
 将区域设置设定为从操作系统获得的 ANSI 代码页。  
  
 `setlocale( LC_ALL, "<localename>" );`  
 将区域设置设定为由 *\<localename\>* 指示的区域设置名称。  
  
 `setlocale( LC_ALL, "<language>_<country>" );`  
 将区域设置设定为由 *\<language\>* 和 *\<country\>* 指示的语言和国家\/地区，以及从主机操作系统获得的默认代码页。  
  
 `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`  
 将区域设置设定为由 *\<language\>*、*\<country\>* 和 *\<code\_page\>* 字符串指示的语言、国家\/地区和代码页。  你可以使用语言、国家\/地区和代码页的各种组合。  例如，此调用会将区域设置设定为“法语\(加拿大\)”并使用代码页 1252：  
  
 `setlocale( LC_ALL, "French_Canada.1252" );`  
  
 此调用会将区域设置设定为“法语\(加拿大\)”并使用默认 ANSI 代码页：  
  
 `setlocale( LC_ALL, "French_Canada.ACP" );`  
  
 此调用会将区域设置设定为“法语\(加拿大\)”并使用默认 OEM 代码页：  
  
 `setlocale( LC_ALL, "French_Canada.OCP" );`  
  
 `setlocale( LC_ALL, "<language>" );`  
 将区域设置设定为由 *\<language\>* 指示的语言，为指定的语言使用默认国家\/地区，为从主机操作系统获取的国家\/地区使用用户默认的 ANSI 代码页。  例如，以下对 `setlocale` 的调用在功能上是等效的：  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 `setlocale( LC_ALL, "English" );`  
  
 `setlocale( LC_ALL, "English_United States.1252" );`  
  
 建议使用第一种形式以实现较高的性能和可维护性。  
  
 `setlocale( LC_ALL, ".<code_page>" );`  
 将代码页设置为由 *\<code\_page\>* 指示的值，以及指定代码页的默认国家\/地区和语言（由主机操作系统定义）。  
  
 类别必须是 `LC_ALL` 或 `LC_CTYPE` 才能影响代码页的更改。  例如，如果主机操作系统的默认国家\/地区和语言为“美国”和“英语”，则以下两个对 `setlocale` 的调用在功能上是等效的：  
  
 `setlocale( LC_ALL, ".1252" );`  
  
 `setlocale( LC_ALL, "English_United States.1252");`  
  
 有关详细信息，请参阅[C\/C\+\+ 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 [setlocale](../../preprocessor/setlocale.md) 杂注指令。  
  
 函数 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) 用于控制 `setlocale` 是否影响程序中所有线程的区域设置或仅影响调用线程的区域设置。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`setlocale`|\<locale.h\>|  
|`_wsetlocale`|\<locale.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```css  
// crt_setlocale.c  
//   
// This program demonstrates the use of setlocale when  
// using two independent threads.  
//  
  
#include <locale.h>  
#include <process.h>  
#include <windows.h>  
#include <stdio.h>  
#include <time.h>  
  
#define BUFF_SIZE 100  
  
// Retrieve the date in the current  
// locale's format.  
int get_date(unsigned char* str)  
{  
    __time64_t ltime;  
    struct tm  thetime;  
  
    // Retrieve the current time  
    _time64(&ltime);  
    _gmtime64_s(&thetime, &ltime);  
  
    // Format the current time structure into a string  
    // "%#x" is the long date representation in the  
    // current locale  
    if (!strftime((char *)str, BUFF_SIZE, "%#x",   
                  (const struct tm *)&thetime))  
    {  
        printf("strftime failed!\n");  
        return -1;  
    }  
    return 0;  
}  
  
// This thread sets its locale to the argument  
// and prints the date.  
uintptr_t __stdcall SecondThreadFunc( void* pArguments )  
{  
    unsigned char str[BUFF_SIZE];  
    char * locale = (char *)pArguments;  
  
    // Set the thread locale  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, locale));  
  
    // Retrieve the date string from the helper function  
    if (get_date(str) == 0)  
    {  
        printf("The date in %s locale is: '%s'\n", locale, str);  
    }  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
// The main thread sets the locale to English   
// and then spawns a second thread (above) and prints the date.  
int main()  
{   
    HANDLE          hThread;  
    unsigned        threadID;  
    unsigned char   str[BUFF_SIZE];  
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
  
    // Set the locale of the main thread to US English.  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "en-US"));  
  
    // Create the second thread with a German locale.  
    // Our thread function takes an argument of the locale to use.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,  
                                      "de-DE", 0, &threadID );  
  
    if (get_date(str) == 0)  
    {  
        // Retrieve the date string from the helper function  
        printf("The date in en-US locale is: '%s'\n\n", str);  
    }  
  
    // Wait for the created thread to finish.  
    WaitForSingleObject( hThread, INFINITE );  
  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
  **线程区域设置现在设置为 en\-US。**  
**en\-US 区域设置中的时间为：“Wednesday, May 12, 2004”**  
**线程区域设置现在设置为 de\-DE。**  
**de\-DE 区域设置中的时间为：“Mittwoch, 12.  Mai 2004”**    
## .NET Framework 等效项  
 [System::Globalization::CultureInfo Class](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)  
  
## 请参阅  
 [区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)