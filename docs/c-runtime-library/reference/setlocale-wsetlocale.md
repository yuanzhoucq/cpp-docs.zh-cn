---
title: setlocale、_wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
ms.openlocfilehash: 618b3e58a52e89561439fe76bf1b30e3cbbce001
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356200"
---
# <a name="setlocale-wsetlocale"></a>setlocale、_wsetlocale

设置或检索运行时区域设置。

## <a name="syntax"></a>语法

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>参数

*category*<br/>
受区域设置影响的分类。

*locale*<br/>
区域设置说明符。

## <a name="return-value"></a>返回值

如果提供了有效*区域设置*并*类别*，则返回指向与指定关联的字符串的指针*区域设置*并*类别*。 如果*区域设置*或*类别*无效，则返回 null 指针，但不更改程序的当前区域设置。

例如，调用

```C
setlocale( LC_ALL, "en-US" );
```

设置所有类别，只返回该字符串

```Output
en-US
```

可以将复制返回的字符串**setlocale**还原该程序的区域设置信息的一部分。 全局或线程本地存储用于返回的字符串**setlocale**。 稍后调用**setlocale**覆盖字符串，这会使之前调用返回的字符串指针。

## <a name="remarks"></a>备注

使用**setlocale**函数来设置、 更改或查询的一部分或由指定的当前程序区域设置信息的所有*区域设置*并*类别*。 *区域设置*指的是可以自定义应用程序的某些方面的局部性 （国家/地区和语言）。 一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。 如果您设置*区域设置*为具有多个窗体在您的计算机上受支持的语言的默认字符串，应检查**setlocale**返回值以确定哪种语言为有效。 例如，如果您设置*区域设置*为"chinese"的返回值可以是"简体中文"或"中文-繁体"。

**_wsetlocale**是宽字符版本**setlocale**;*区域设置*参数和返回值 **_wsetlocale**都是宽字符字符串。 **_wsetlocale**并**setlocale**行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

*类别*参数指定受影响的程序的区域设置信息部分。 用于的宏*类别*和及其影响的程序部分如下所示：

|*类别*标志|影响|
|-|-|
| **LC_ALL** | 以下列出了所有类别。 |
| LC_COLLATE | **Strcoll**， **_stricoll**， **wcscoll**， **_wcsicoll**， **strxfrm**， **_strncoll**， **_strnicoll**， **_wcsncoll**， **_wcsnicoll**，并且**wcsxfrm**函数。 |
| LC_CTYPE | 字符处理函数 (除**isdigit**， **isxdigit**， **mbstowcs**，以及**mbtowc**，不受影响)。 |
| **LC_MONETARY** | 返回的货币格式信息**localeconv**函数。 |
| LC_NUMERIC | 小数点字符格式化的输出例程 (如**printf**)、 数据转换例程，以及返回的非货币格式设置信息**localeconv**。 除小数点字符之外**LC_NUMERIC**集千位分隔符和分组控制返回字符串[localeconv](localeconv.md)。 |
| LC_TIME | **Strftime**并**wcsftime**函数。 |

此函数验证类别参数。 如果类别参数不是上表中提供的值之一，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，该函数将设置**errno**到**EINVAL** ，并返回**NULL**。

*区域设置*参数是指向指定的区域设置的字符串。 有关格式的详细信息*区域设置*自变量，请参阅[区域设置名称、 语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 *locale* 指向一个空字符串，则区域设置是实现定义的本机环境。 值为**C**指定最小为 C 转换 ANSI 符合的环境。 **C**区域设置假设所有**char**数据类型为 1 个字节，并且其值始终是小于 256。

在程序启动时，将执行以下语句的等效项：

`setlocale( LC_ALL, "C" );`

*区域设置*参数可使用区域设置名称、 语言字符串、 语言字符串和国家/地区代码、 代码页或语言字符串、 国家/地区代码和代码页。 可用区域设置名称、语言、国家/地区代码和代码页集包含 Windows NLS API 支持的所有内容，要求每个字符对应两个以上的字节的代码页除外（如 UTF-7 和 UTF-8）。 如果提供的 utf-7 或 utf-8 的代码页值**setlocale**将失败并返回**NULL**。 支持的区域设置名称的一套**setlocale**中所述[区域设置名称、 语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 支持的语言和国家/地区字符串的一套**setlocale**中列出[语言字符串](../../c-runtime-library/language-strings.md)并[国家/地区字符串](../../c-runtime-library/country-region-strings.md)。 建议对嵌入到代码中或序列化到存储中的区域设置字符串的性能和可维护性使用区域设置名称格式。 与语言和国家/地区名称格式相比，操作系统的更新更改区域设置名称字符串的可能性会小一些。

作为传递的 null 指针*区域设置*参数告知**setlocale**查询而不是设置国际环境。 如果*区域设置*参数为 null 指针，该程序的当前区域设置不会更改。 相反， **setlocale**与关联的字符串返回指向*类别*线程的当前区域设置。 如果*类别*自变量是**LC_ALL**，该函数返回一个字符串，指示每个类别，之间用分号分隔的当前设置。 例如，调用的顺序

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

返回

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

这是与之关联的字符串**LC_ALL**类别。

下面的示例适用于**LC_ALL**类别。 可使用字符串“.OCP”或“.ACP”而非代码页号来分别指定用户默认的 OEM 代码页和用户默认的 ANSI 代码页的用法。

- `setlocale( LC_ALL, "" );`

   将区域设置设定为默认值，该值是从操作系统获得的用户默认的 ANSI 代码页。

- `setlocale( LC_ALL, ".OCP" );`

   将设置区域显式设置为从操作系统获得的当前 OEM 代码页。

- `setlocale( LC_ALL, ".ACP" );`

   将区域设置设定为从操作系统获得的 ANSI 代码页。

- `setlocale( LC_ALL, "<localename>" );`

   将区域设置设定为由 *\<localename>* 指示的区域设置名称。

- `setlocale( LC_ALL, "<language>_<country>" );`

   将区域设置设定为由 *\<language>* 和 *\<country>* 指示的语言和国家/地区，以及从主机操作系统获得的默认代码页。

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   设置语言、 国家/地区和代码页的区域设置为由 *\<语言 >*， *\<国家/地区 >*，以及 *\<code_page>* 字符串。 你可以使用语言、国家/地区和代码页的各种组合。 例如，此调用会将区域设置设定为“法语(加拿大)”并使用代码页 1252：

   `setlocale( LC_ALL, "French_Canada.1252" );`

   此调用会将区域设置设定为“法语(加拿大)”并使用默认 ANSI 代码页：

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   此调用会将区域设置设定为“法语(加拿大)”并使用默认 OEM 代码页：

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   将区域设置设定为由 *\<language>* 指示的语言，为指定的语言使用默认国家/地区，为从主机操作系统获取的国家/地区使用用户默认的 ANSI 代码页。 例如，以下调用**setlocale**在功能上等效：

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   建议使用第一种形式以实现较高的性能和可维护性。

- `setlocale( LC_ALL, ".<code_page>" );`

   将代码页设置为由 *<code_page>* 指示的值，以及指定代码页的默认国家/地区和语言（由主机操作系统定义）。

类别必须是**LC_ALL**或**LC_CTYPE**实现代码页的更改。 例如，如果默认国家/地区和主机操作系统的语言是"美国"和"英语"，以下两个调用到**setlocale**在功能上等效：

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

有关详细信息，请参阅 [C/C++ 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 [setlocale](../../preprocessor/setlocale.md) pragma 指令。

该函数[_configthreadlocale](configthreadlocale.md)是否用于控制**setlocale**会影响程序中的所有线程的区域设置或仅调用线程的区域设置。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
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

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>请参阅

[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
