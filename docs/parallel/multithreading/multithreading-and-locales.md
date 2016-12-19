---
title: "多线程和区域设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "区域设置 [C++], 多线程处理"
  - "多线程处理 [C++], 区域设置"
  - "每线程区域设置"
  - "线程处理 [C++], 区域设置"
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多线程和区域设置
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C 运行库和标准 C\+\+ 库都支持更改程序的区域设置。  本主题讨论在多线程应用程序中使用这两个库的区域设置功能时出现的问题。  
  
## 备注  
 使用 C 运行库，您可以使用 `_beginthread` 和 `_beginthreadex` 函数创建多线程应用程序。  本主题仅涵盖使用这些函数创建的多线程应用程序。  有关详细信息，请参阅[\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)。  
  
 要使用 C 运行库更改区域设置，请使用 [setlocale](../../preprocessor/setlocale.md) 函数。  在以前版本的 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 中，此函数始终修改整个应用程序中的区域设置。  现在，支持在每线程基础上设置区域设置。  这是使用 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) 函数实现的。  要指定该 [setlocale](../../preprocessor/setlocale.md) 仅应更改当前线程中的区域设置，请在该线程中调用 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。  相反，调用 `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` 将导致该线程使用全局区域设置，对该线程中 [setlocale](../../preprocessor/setlocale.md) 的任何调用将更改未显式启用每线程区域设置的所有线程中的区域设置。  
  
 要使用 C\+\+ 运行库更改区域设置，请使用 [locale 类](../../standard-library/locale-class.md)。  通过调用 [locale::global](../Topic/locale::global.md) 方法，可以更改未显式启用每线程区域设置的每个线程中的区域设置。  要更改应用程序的单个线程或部分的区域设置，只需在该线程或代码部分中创建 `locale` 对象的实例。  
  
> [!NOTE]
>  调用 [locale::global](../Topic/locale::global.md) 将同时更改标准 C\+\+ 库和 C 运行库的区域设置。  但是，调用 [setlocale](../../preprocessor/setlocale.md) 仅更改 C 运行库的区域设置；标准 C\+\+ 库不受影响。  
  
 以下示例显示如何使用 [setlocale](../../preprocessor/setlocale.md) 函数、[locale 类](../../standard-library/locale-class.md) 和 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) 函数在几个不同的方案中更改应用程序的区域设置。  
  
## 示例  
 在此示例中，主线程生成两个子线程。  第一个线程（线程 A）通过调用 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 启用每线程区域设置。  第二个线程（线程 B）与主线程一样，不启用每线程区域设置。  然后，线程 A 继续使用 C 运行库的 [setlocale](../../preprocessor/setlocale.md) 函数更改区域设置。  
  
 由于线程 A 启用了每线程区域设置，只有线程 A 中的 C 运行库函数开始使用“法国”区域设置。  线程 B 以及主线程中的 C 运行库函数继续使用“C”区域设置。  此外，由于 [setlocale](../../preprocessor/setlocale.md) 并不影响标准 C\+\+ 库区域设置，所有标准 C\+\+ 库对象继续使用“C”区域设置。  
  
```  
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
  
  **\[线程 A\] 每线程区域设置处于启用状态。**  
**\[线程 A\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 A\] locale::global 设为“C”**  
**\[线程 B\] 每线程区域设置处于禁用状态。**  
**\[线程 B\] CRT 区域设置设为“C”**  
**\[线程 B\] locale::global 设为“C”**  
**\[线程 main\] 每线程区域设置处于禁用状态。**  
**\[线程 main\] CRT 区域设置设为“C”**  
**\[线程 main\] locale::global 设为“C”**   
## 示例  
 在此示例中，主线程生成两个子线程。  第一个线程（线程 A）通过调用 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 启用每线程区域设置。  第二个线程（线程 B）与主线程一样，不启用每线程区域设置。  然后，线程 A 继续使用标准 C\+\+ 库的 [locale::global](../Topic/locale::global.md) 方法更改区域设置。  
  
 由于线程 A 启用了每线程区域设置，只有线程 A 中的 C 运行库函数开始使用“法国”区域设置。  线程 B 以及主线程中的 C 运行库函数继续使用“C”区域设置。  但是，由于 [locale::global](../Topic/locale::global.md) 方法会“全局性地”更改区域设置，所有线程中的所有标准 C\+\+ 库对象都开始使用“法国”区域设置。  
  
```  
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
  
  **\[线程 A\] 每线程区域设置处于启用状态。**  
**\[线程 A\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 A\] locale::global 设为“French\_France.1252”**  
**\[线程 B\] 每线程区域设置处于禁用状态。**  
**\[线程 B\] CRT 区域设置设为“C”**  
**\[线程 B\] locale::global 设为“French\_France.1252”**  
**\[线程 main\] 每线程区域设置处于禁用状态。**  
**\[线程 main\] CRT 区域设置设为“C”**  
**\[线程 main\] locale::global 设为“French\_France.1252”**   
## 示例  
 在此示例中，主线程生成两个子线程。  第一个线程（线程 A）通过调用 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 启用每线程区域设置。  第二个线程（线程 B）与主线程一样，不启用每线程区域设置。  然后，线程 B 继续使用 C 运行库的 [setlocale](../../preprocessor/setlocale.md) 函数更改区域设置。  
  
 由于线程 B 没有启用每线程区域设置，线程 B 以及主线程中的 C 运行库函数开始使用“法国”区域设置。  由于线程 A 启用了每线程区域设置，线程 A 中的 C 运行库函数继续使用“C”区域设置。  此外，由于 [setlocale](../../preprocessor/setlocale.md) 并不影响标准 C\+\+ 库区域设置，所有标准 C\+\+ 库对象继续使用“C”区域设置。  
  
```  
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
  
  **\[线程 B\] 每线程区域设置处于禁用状态。**  
**\[线程 B\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 B\] locale::global 设为“C”**  
**\[线程 A\] 每线程区域设置处于启用状态。**  
**\[线程 A\] CRT 区域设置设为“C”**  
**\[线程 A\] locale::global 设为“C”**  
**\[线程 main\] 每线程区域设置处于禁用状态。**  
**\[线程 main\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 main\] locale::global 设为“C”**   
## 示例  
 在此示例中，主线程生成两个子线程。  第一个线程（线程 A）通过调用 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 启用每线程区域设置。  第二个线程（线程 B）与主线程一样，不启用每线程区域设置。  然后，线程 B 继续使用标准 C\+\+ 库的 [locale::global](../Topic/locale::global.md) 方法更改区域设置。  
  
 由于线程 B 没有启用每线程区域设置，线程 B 以及主线程中的 C 运行库函数开始使用“法国”区域设置。  由于线程 A 启用了每线程区域设置，线程 A 中的 C 运行库函数继续使用“C”区域设置。  但是，由于 [locale::global](../Topic/locale::global.md) 方法会“全局性地”更改区域设置，所有线程中的所有标准 C\+\+ 库对象都开始使用“法国”区域设置。  
  
```  
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
  
  **\[线程 B\] 每线程区域设置处于禁用状态。**  
**\[线程 B\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 B\] locale::global 设为“French\_France.1252”**  
**\[线程 A\] 每线程区域设置处于启用状态。**  
**\[线程 A\] CRT 区域设置设为“C”**  
**\[线程 A\] locale::global 设为“French\_France.1252”**  
**\[线程 main\] 每线程区域设置处于禁用状态。**  
**\[线程 main\] CRT 区域设置设为“French\_France.1252”**  
**\[线程 main\] locale::global 设为“French\_France.1252”**   
## 请参阅  
 [针对旧代码的多线程支持 \(Visual C\+\+\)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [国际化](../../c-runtime-library/internationalization.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\<clocale\>](../../standard-library/clocale.md)   
 [\<locale\>](../../standard-library/locale.md)   
 [locale 类](../../standard-library/locale-class.md)