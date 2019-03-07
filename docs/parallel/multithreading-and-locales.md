---
title: 多线程和区域设置
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: c12a3fa1922db7a1ec0a7bcd43ddf09000d97961
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293597"
---
# <a name="multithreading-and-locales"></a>多线程和区域设置

C 运行时库和 c + + 标准库更改您的程序的区域设置提供支持。 本主题讨论使用这两个库中的多线程应用程序的区域设置功能时出现的问题。

## <a name="remarks"></a>备注

使用 C 运行时库，可以创建使用多线程应用程序`_beginthread`和`_beginthreadex`函数。 本主题仅介绍使用这些函数创建的多线程应用程序。 有关详细信息，请参阅[_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)。

若要更改使用 C 运行时库的区域设置，请使用[setlocale](../preprocessor/setlocale.md)函数。 在以前版本的 Visual c + + 中，此函数始终会修改整个应用程序中的区域设置。 没有用于设置针对每个线程区域设置现在支持。 这是使用[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)函数。 若要指定的[setlocale](../preprocessor/setlocale.md)才应更改当前线程调用中的区域设置`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`该线程中。 相反，调用`_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)`该线程使用全局区域设置，以及对任何调用将导致[setlocale](../preprocessor/setlocale.md) ，线程将更改尚未显式启用每个线程区域设置的所有线程的区域设置。

若要更改使用 c + + 运行时库的区域设置，请使用[locale 类](../standard-library/locale-class.md)。 通过调用[locale:: global](../standard-library/locale-class.md#global)方法，可以更改未显式启用每个线程区域设置的每个线程的区域设置。 若要更改单个线程或应用程序的一部分的区域设置，只需创建的实例`locale`该线程或代码部分中的对象。

> [!NOTE]
> 调用[locale:: global](../standard-library/locale-class.md#global)对 c + + 标准库和 C 运行时库的更改区域设置。 但是，调用[setlocale](../preprocessor/setlocale.md)仅更改区域设置的 c + + 标准库; C 运行时库不会受到影响。

下面的示例演示如何使用[setlocale](../preprocessor/setlocale.md)函数， [locale 类](../standard-library/locale-class.md)，并[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)函数更改中的应用程序的区域设置多个不同的方案。

## <a name="example"></a>示例

在此示例中，主线程将生成两个子线程。 第一个线程，线程 A，通过调用允许每个线程区域设置`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二个线程、 线程 B，以及主线程，则不要启用每个线程区域设置。 然后继续进行，若要更改区域设置使用的线程[setlocale](../preprocessor/setlocale.md) C 运行时库函数。

由于线程 A 了每个线程区域设置已启用，仅在线程 A 入门中使用"法国"区域设置的 C 运行时库函数。 C 运行时库函数线程 B 中和在主线程继续使用"C"区域设置。 此外，由于[setlocale](../preprocessor/setlocale.md)不会影响 c + + 标准库区域设置，继续使用"C"区域设置对象的所有 c + + 标准库。

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>示例

在此示例中，主线程将生成两个子线程。 第一个线程，线程 A，通过调用允许每个线程区域设置`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二个线程、 线程 B，以及主线程，则不要启用每个线程区域设置。 然后继续进行，若要更改区域设置使用的线程[locale:: global](../standard-library/locale-class.md#global) c + + 标准库的方法。

由于线程 A 了每个线程区域设置已启用，仅在线程 A 入门中使用"法国"区域设置的 C 运行时库函数。 C 运行时库函数线程 B 中和在主线程继续使用"C"区域设置。 但是，由于[locale:: global](../standard-library/locale-class.md#global)方法"全局"更改区域设置，所有线程中的所有 c + + 标准库对象开始使用"法国"区域设置。

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example"></a>示例

在此示例中，主线程将生成两个子线程。 第一个线程，线程 A，通过调用允许每个线程区域设置`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二个线程、 线程 B，以及主线程，则不要启用每个线程区域设置。 线程 B，然后继续进行，若要更改区域设置使用[setlocale](../preprocessor/setlocale.md) C 运行时库函数。

由于线程 B 没有启用的每个线程区域设置，C 运行时库函数线程 B 以及主线程中开始使用"法语"区域设置。 线程 A 继续使用"C"区域设置，因为线程 A 已启用的每个线程区域设置中的 C 运行时库函数。 此外，由于[setlocale](../preprocessor/setlocale.md)不会影响 c + + 标准库区域设置，继续使用"C"区域设置对象的所有 c + + 标准库。

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>示例

在此示例中，主线程将生成两个子线程。 第一个线程，线程 A，通过调用允许每个线程区域设置`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二个线程、 线程 B，以及主线程，则不要启用每个线程区域设置。 线程 B，然后继续进行，若要更改区域设置使用[locale:: global](../standard-library/locale-class.md#global) c + + 标准库的方法。

由于线程 B 没有启用的每个线程区域设置，C 运行时库函数线程 B 以及主线程中开始使用"法语"区域设置。 线程 A 继续使用"C"区域设置，因为线程 A 已启用的每个线程区域设置中的 C 运行时库函数。 但是，由于[locale:: global](../standard-library/locale-class.md#global)方法"全局"更改区域设置，所有线程中的所有 c + + 标准库对象开始使用"法国"区域设置。

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>请参阅

[针对旧代码的多线程支持 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[国际化](../c-runtime-library/internationalization.md)<br/>
[区域设置](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale 类](../standard-library/locale-class.md)
