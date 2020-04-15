---
title: _configthreadlocale
ms.date: 4/2/2020
api_name:
- _configthreadlocale
- _o__configthreadlocale
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 46983843e128b59df89722c8d4694c30a858011f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348543"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

配置每个线程的区域设置选项。

## <a name="syntax"></a>语法

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>参数

*per_thread_locale_type*<br/>
要设置的选项。 其中一个选项已在下表中列出。

## <a name="return-value"></a>返回值

以前的每个线程区域设置状态 **（_DISABLE_PER_THREAD_LOCALE**或 **_ENABLE_PER_THREAD_LOCALE），** 或失败时为 -1。

## <a name="remarks"></a>备注

**_configurethreadlocale**函数用于控制线程特定区域设置的使用。 使用这些*per_thread_locale_type*选项之一指定或确定每个线程区域设置状态：

| 选项 | 说明 |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | 使当前线程使用特定于线程的区域设置。 在此线程中**设置区域设置的**后续调用仅影响线程自己的区域设置。 |
| **_DISABLE_PER_THREAD_LOCALE** | 使当前线程使用全局区域设置。 在此线程中**设置区域设置的**后续调用会影响使用全局区域设置的其他线程。 |
| **0** | 检索此特定线程的当前设置。 |

这些函数影响**集区域设置****、_tsetlocale、_wsetlocale**和 **_setmbcp**的行为。 **_wsetlocale** 禁用每个线程区域设置时，任何后续设置**区域设置**或 **_wsetlocale**调用都更改使用全局区域设置的所有线程的区域设置。 启用每个线程区域设置时，**设置区域设置**或 **_wsetlocale**只会影响当前线程区域设置。

如果使用 **_configurethreadlocale**启用每个线程区域设置，我们建议您调用**setlocale**或 **_wsetlocale，** 以便立即在该线程中设置首选区域设置。

如果*per_thread_locale_type*不是表中列出的值之一，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回 -1。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>示例

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
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
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

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

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
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

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>另请参阅

[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多线程和区域设置](../../parallel/multithreading-and-locales.md)<br/>
