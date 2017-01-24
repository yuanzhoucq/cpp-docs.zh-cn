---
title: "qsort_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "qsort_s"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "qsort_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "数组 [C++], 排序"
  - "qsort_s 函数"
  - "快速排序算法"
  - "对数组进行排序"
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行快速排序。  [qsort](../../c-runtime-library/reference/qsort.md) 的一个版本提供安全增强功能，正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### 参数  
 `base`  
 目标数组的开头。  
  
 `num`  
 元素的数组大小。  
  
 `width`  
 以字节为单位的元素大小。  
  
 `compare`  
 比较函数。  第一个参数是 `context` 指针。  第二个参数是指向将要搜索的 `key`。  第三个参数是指向数组元素与 `key`进行比较。  
  
 `context`  
 一个指向上下文的指针，可以是任何 `compare` 例程需要访问的对象。  
  
## 备注  
 `qsort_s` 函数可实现快速排序算法对一个 `num` 元素，每个 `width` 字节数组进行排序。  参数 `base` 是一个指向要排序数组的基类的指针。  `qsort_s` 重写该已排序元素的数组。  参数 `compare` 是指向一用户提供的程序用来比较两个数组元素并返回指定其关系的值。  在排序时，`qsort_s` 调用程序 `compare` 一次或多次，并在每次调用时将指针传给两个数组元素：  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 例程必须比较元素然后返回下列值之一：  
  
|返回值|说明|  
|---------|--------|  
|\< 0|`elem1` 小于 `elem2`|  
|0|`elem1` 等效于 `elem2`|  
|\> 0|`elem1` 大于 `elem2`|  
  
 正如所定义的比较函数，数组以递增排序。  若要降序排序一个数组，在比较函数中反转“大于”和“小于“的意思。  
  
 如果传递给函数的是无效参数，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数将返回并将 `EINVAL` 设置为 `errno`。  有关更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 错误情况  
  
|键|base|compare|num|width|errno|  
|-------|----------|-------------|---------|-----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|\<\= 0|`EINVAL`|  
|any|any|`NULL`|any|any|`EINVAL`|  
  
 `qsort_s` 的方法与 `qsort` 相同，但是具有 `context` 参数并设置为 `errno`。  通过传递一个 `context` 参数，比较函数可以通过元素指针使用对象指针功能地访问对象或不可访问的其他信息。  因为通过使用静态变量共享可用信息传递给 `compare` 函数，`context` 可用于避免重新进入产生的缺陷中，`context` 参数使 `qsort_s`更安全。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`qsort_s`|\<stdlib.h\> and \<search.h\>|  
  
 有关其他兼容性详细信息，请参阅简介中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
 **Libraries:** 的所有版本 [CRT 库功能](../../c-runtime-library/crt-library-features.md).  
  
## 示例  
 下面的示例演示如何在 `qsort_s` ``  函数中使用 `context` 参数。  `context` 参数使更容易执行线程安全排序。  而不是使用必须同步确保线程安全性的静态变量，在每次排序中传递一个不同的 `context` 参数。  在本示例中，语言环境对象被用作 `context` 参数。  
  
```  
// crt_qsort_s.cpp  
// compile with: /EHsc /MT  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S in that codepage and \x00a4  
// is the n tilde.  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
#define SPANISH_LOCALE "Spanish_Spain.850"  
#define ENGLISH_LOCALE "English_US.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S and \x001f for the n tilde.  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
#define SPANISH_LOCALE "Spanish_Spain.1252"  
#define ENGLISH_LOCALE "English_US.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making sort_array vulnerable to thread  
// conflicts.  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char s1[256];  
    char s2[256];  
    strcpy_s(s1, 256, *(char**)str1);  
    strcpy_s(s2, 256, *(char**)str2);  
    _strlwr_s( s1, sizeof(s1) );  
    _strlwr_s( s2, sizeof(s2) );  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(s1,   
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);  
  
}  
  
void sort_array(char *array[], int num, locale &loc)  
{  
    qsort_s(array, num, sizeof(char*), compare, &loc);  
}  
  
void print_array(char *a[], int c)  
{  
   for (int i = 0; i < c; i++)  
     printf("%s ", a[i]);  
   printf("\n");  
  
}  
  
void sort_german(void * Dummy)  
{  
   sort_array(array1, 6, locale(GERMAN_LOCALE));  
}  
  
void sort_spanish(void * Dummy)  
{     
   sort_array(array2, 3, locale(SPANISH_LOCALE));       
}  
  
void sort_english(void * Dummy)  
{     
   sort_array(array3, 3, locale(ENGLISH_LOCALE));     
}  
  
int main( )  
{  
  
   int i;  
   HANDLE threads[3];  
  
   printf("Unsorted input:\n");  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
   // Create several threads that perform sorts in different  
   // languages at the same time.   
  
   threads[0] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_german , 0, NULL));  
   threads[1] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_spanish, 0, NULL));  
   threads[2] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_english, 0, NULL));  
  
   for (i = 0; i < 3; i++)  
   {  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
      {  
         printf("Error creating threads.\n");  
         exit(1);  
      }  
   }  
  
   // Wait until all threads have terminated.  
   WaitForMultipleObjects(3, threads, true, INFINITE);  
  
   printf("Sorted output: \n");  
  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
}  
```  
  
## 示例输出  
  
```  
Unsorted input:  
weiß weis annehmen weizen Zeit weit   
Español España espantado   
table tableux tablet   
Sorted output:   
annehmen weiß weis weit weizen Zeit   
España Español espantado   
table tablet tableux  
```  
  
## .NET Framework 等效项  
 <xref:System.Collections.ArrayList.Sort%2A>  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)