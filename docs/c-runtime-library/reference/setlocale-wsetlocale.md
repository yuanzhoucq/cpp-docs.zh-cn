---
title: setlocale, _wsetlocale
description: 描述 Microsoft C 运行时 (CRT) 库函数 setlocale 和 _wsetlocale 。
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 812aab43667416a5892d8e24d03d0e67cad8d0ac
ms.sourcegitcommit: b51703a96ee35ee2376d5f0775b70f03ccbe6d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88086989"
---
# <a name="no-locsetlocale-no-loc_wsetlocale"></a>setlocale, _wsetlocale

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

*类别*\
受区域设置影响的分类。

*本地*\
区域设置说明符。

## <a name="return-value"></a>返回值

如果提供了有效的*区域设置*和*类别*，则返回指向与指定的*区域设置*和*类别*关联的字符串的指针。 如果*区域设置*或*类别*无效，则返回空指针，并且不更改程序的当前区域设置。

例如，调用

```C
setlocale( LC_ALL, "en-US" );
```

设置所有类别，只返回该字符串

```Output
en-US
```

你可以复制由 `setlocale` 返回的字符串以还原程序的区域设置信息的该部分。 全局或线程本地存储用于由 `setlocale` 返回的字符串。 稍后调用 `setlocale` 将覆盖字符串，这将使之前调用返回的字符串指针无效。

## <a name="remarks"></a>备注

使用 `setlocale` 函数设置、更改或查询由*区域设置*和*类别*指定的某些或全部当前程序区域设置信息。 *区域设置*是指可以为其自定义程序的某些方面的区域 (国家/地区和语言) 。 一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。 如果将 "*区域*设置" 设置为在计算机上支持多个窗体的语言的默认字符串，则应检查 `setlocale` 返回值以查看哪种语言有效。 例如，如果将 "*区域*设置" 设置为 "中文"，则返回值可能是 "简体中文" 或 "繁体中文"。

`_wsetlocale`是的宽字符版本; 的 `setlocale` *区域设置*参数和的返回值 `_wsetlocale` 都是宽字符字符串。 除此以外，`_wsetlocale` 和 `setlocale` 的行为完全相同。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|

*Category*参数指定程序的受影响的部分区域设置信息。 用于*类别*的宏及其影响的程序的部分如下所示：

|*类别*标志|影响|
|-|-|
| `LC_ALL` | 以下列出了所有类别。 |
| `LC_COLLATE` | `strcoll`、`_stricoll`、`wcscoll`、`_wcsicoll`、`strxfrm`、`_strncoll`、`_strnicoll`、`_wcsncoll`、`_wcsnicoll` 和 `wcsxfrm` 函数。 |
| `LC_CTYPE` | 字符处理函数（不受影响的 `isdigit`、`isxdigit`、`mbstowcs` 和 `mbtowc` 除外）。 |
| `LC_MONETARY` | `localeconv` 函数返回的货币格式信息。 |
| `LC_NUMERIC` | 格式化输出例程（例如 `printf`）、数据转换例程和 `localeconv` 所返回的非货币格式设置信息的十进制点字符。 除小数点字符之外，`LC_NUMERIC` 还设置 [localeconv](localeconv.md) 返回的千位分隔符和分组控制字符串。 |
| `LC_TIME` | `strftime` 和 `wcsftime` 函数。 |

此函数验证类别参数。 如果类别参数不是上表中提供的值之一，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `NULL`。

*Locale*参数是指向指定区域设置的字符串的指针。 有关*区域设置*参数格式的信息，请参阅[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 *locale* 指向一个空字符串，则区域设置是实现定义的本机环境。 `C` 的值为 C 转换指定最小的符合 ANSI 标准的环境。 `C` 区域设置假设所有 ``char`` 数据类型为 1 字节，并且其值始终小于 256。

在程序启动时，将执行以下语句的等效项：

`setlocale( LC_ALL, "C" );`

*区域设置*参数可以采用区域设置名称、语言字符串、语言字符串和国家/地区代码、代码页或语言字符串、国家/地区代码和代码页。 可用区域设置名称、语言、国家/地区代码和代码页集包含 Windows NLS API 支持的所有功能。 [区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中介绍了 `setlocale` 所支持的区域设置名称集合。 [语言字符串](../../c-runtime-library/language-strings.md)和[国家/地区字符串](../../c-runtime-library/country-region-strings.md)中列出了 `setlocale` 所支持的语言和国家/地区字符串集合。 建议对嵌入到代码中或序列化到存储中的区域设置字符串的性能和可维护性使用区域设置名称格式。 与语言和国家/地区名称格式相比，操作系统的更新更改区域设置名称字符串的可能性会小一些。

作为*区域设置*参数传递的 null 指针告知 `setlocale` 查询而不是设置国际环境。 如果*locale*参数为 null 指针，则不更改程序的当前区域设置。 相反， `setlocale` 返回指向与线程的当前区域设置的*类别*关联的字符串的指针。 如果*category*参数为 `LC_ALL` ，则该函数将返回一个字符串，该字符串指示每个类别的当前设置（用分号分隔）。 例如，调用的顺序

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

它是与 `LC_ALL` 类别关联的字符串。

以下示例与 `LC_ALL` 类别相关。 字符串 "。OCP "and"。可以使用 ACP "而不是代码页号来指定用户默认的 OEM 代码页和该区域设置名称的用户默认的 ANSI 代码页。

- `setlocale( LC_ALL, "" );`

   将区域设置设定为默认值，该值是从操作系统获得的用户默认的 ANSI 代码页。 区域设置名称设置为[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)返回的值。 将代码页设置为[GetACP](/windows/win32/api/winnls/nf-winnls-getacp)返回的值。

- `setlocale( LC_ALL, ".OCP" );`

   将区域设置设置为从操作系统获得的当前 OEM 代码页。 区域设置名称设置为[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)返回的值。 通过[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)将代码页设置为用户默认区域设置名称的[LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, ".ACP" );`

   将区域设置设定为从操作系统获得的 ANSI 代码页。 区域设置名称设置为[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)返回的值。 通过[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)将代码页设置为用户默认区域设置名称的[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<localename>" );`

   将区域设置设置为指示的区域设置名称 *\<localename>* 。 通过[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)将代码页设置为指定的区域设置名称的[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<language>_<country>" );`

   将区域设置设置为所指示的语言和国家/ *\<language>* 地区 *\<country>* ，以及从主机操作系统获得的默认代码页。 通过[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)将代码页设置为指定的区域设置名称的[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   将区域设置设置为 *\<language>* 、和字符串指示的语言、国家/地区和代码页 *\<country>* *\<code_page>* 。 你可以使用语言、国家/地区和代码页的各种组合。 例如，此调用会将区域设置设定为“法语(加拿大)”并使用代码页 1252：

   `setlocale( LC_ALL, "French_Canada.1252" );`

   此调用会将区域设置设定为“法语(加拿大)”并使用默认 ANSI 代码页：

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   此调用会将区域设置设定为“法语(加拿大)”并使用默认 OEM 代码页：

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   将区域设置设置为所指示的语言 *\<language>* ，并为指定的语言使用默认国家/地区，并为该国家/地区使用从主机操作系统获得的用户默认的 ANSI 代码页。 例如，以下对 `setlocale` 的调用在功能上是等效的：

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   建议使用第一种形式以实现较高的性能和可维护性。

- `setlocale( LC_ALL, ".<code_page>" );`

   将代码页设置为由 *<code_page>* 指示的值，以及指定代码页的默认国家/地区和语言（由主机操作系统定义）。

类别必须是 `LC_ALL` 或 `LC_CTYPE` 才能影响代码页的更改。 例如，如果主机操作系统的默认国家/地区和语言为“美国”和“英语”，则以下两个对 `setlocale` 的调用在功能上是等效的：

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

有关详细信息，请参阅 [setlocale](../../preprocessor/setlocale.md) [C/c + + 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)中的杂注指令。

函数 [_configthreadlocale](configthreadlocale.md) 用于控制 `setlocale` 是否影响程序中所有线程的区域设置或仅影响调用线程的区域设置。

## <a name="utf-8-support"></a>UTF-8 支持

从 Windows 10 build 17134 开始 (2018 年4月更新) ，通用 C 运行时支持使用 UTF-8 代码页。 这意味着 `char` 传递给 C 运行时函数的字符串将需要 utf-8 编码格式的字符串。 若要启用 UTF-8 模式，请在使用时使用 "UTF-8" 作为代码页 `setlocale` 。 例如， `setlocale(LC_ALL, ".utf8")` 将使用当前默认 WINDOWS ANSI 代码页 (ACP) 用于区域设置，并使用 utf-8 作为代码页。

调用后 `setlocale(LC_ALL, ".UTF8")` ，你可以将 "" 传递给， 😊 `mbtowcs` 并将其正确地转换为 `wchar_t` 字符串，但之前没有可用于执行此操作的区域设置。

对于 `char` 使用默认 WINDOWS ANSI 代码页（ (ACP) ）的已翻译字符串，也启用了 utf-8 模式。 例如， [`_mkdir("😊")`](../reference/mkdir-wmkdir.md) 当使用 utf-8 代码页时，调用会正确生成包含该表情符号作为文件夹名称的目录，而不需要在运行程序之前将 ACP 更改为 utf-8。 同样， [`_getcwd()`](../reference/getcwd-wgetcwd.md) 在该文件夹内调用将返回 utf-8 编码的字符串。 为实现兼容性，如果 C 区域设置代码页未设置为 UTF-8，则仍将使用 ACP。

C 运行时的以下方面不能使用 utf-8，因为在程序启动过程中设置了 utf-8，并且必须使用默认的 Windows ANSI 代码页 (ACP) ： [`__argv`](../argc-argv-wargv.md) 、 [`_acmdln`](../acmdln-tcmdln-wcmdln.md) 和 [`_pgmptr`](../pgmptr-wpgmptr.md) 。

之前，此支持、 [ `mbrtoc16` `mbrtoc32` 、 ](../reference/mbrtoc16-mbrtoc323.md)、 [ `c16rtomb` `c32rtomb` 和](../reference/c16rtomb-c32rtomb1.md)存在于 utf-8 窄字符串之间，utf-16 (与 `wchar_t` Windows 平台上的相同编码) 和32。 出于兼容性原因，这些 Api 仍只能从 utf-8 转换到 utf-8，而不是通过设置代码页 `setlocale` 。

若要在 Windows 10 之前的操作系统（如 Windows 7）上使用此功能，必须使用 Windows SDK 或更高版本的17134版的[应用程序本地部署](../../windows/universal-crt-deployment.md#local-deployment)或静态链接。 对于17134之前的 Windows 10 操作系统，仅支持静态链接。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`setlocale`|\<locale.h>|
|`_wsetlocale`|\<locale.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale，_wcreate_locale](create-locale-wcreate-locale.md)\
[本地](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)\
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb、_wctomb_l](wctomb-wctomb-l.md)
