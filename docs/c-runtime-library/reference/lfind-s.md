---
title: "_lfind_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lfind_s"
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
  - "lfind_s"
  - "_lfind_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lfind_s 函数"
  - "数组 [CRT], 搜索"
  - "键, 在数组中查找"
  - "lfind_s 函数"
  - "线性搜索"
  - "搜索, 线性"
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _lfind_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行指定键的线性搜索。  [\_lfind](../../c-runtime-library/reference/lfind.md) 的一个版本提供安全增强功能，正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### 参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 要搜索数据的基本指针。  
  
 `num`  
 数组元素的数目。  
  
 `size`  
 数组元素的大小 \(以字节为单位\)。  
  
 `compare`  
 比较程序的指针。  第一个参数是 `context` 指针。  第二个参数是搜索键的指针。  第三个参数是指向数组元素的指针与关键字进行比较。  
  
 `context`  
 在比较函数中可能访问的对象的指针。  
  
## 返回值  
 如果找到键 `_lfind_s`，返回指向数组的元素的指针`base` 匹配`key`。  如果键未找到，`_lfind_s` 返回 `NULL`。  
  
 如果传递给函数的是无效参数，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  
  
### 错误情况  
  
|键|base|compare|num|size|errno|  
|-------|----------|-------------|---------|----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|零|`EINVAL`|  
|any|any|`NULL`|an|any|`EINVAL`|  
  
## 备注  
 `_lfind_s` 函数在包含 `num`个元素的数组中执行线性搜索查找值`key`，其中每个元素有 `width` 字节。  与 `bsearch_s`不同，`_lfind_s` 不需要排序数组。  参数 `base` 是一个指向要查找数组的基类的指针。  参数 `compare` 是指向一用户提供的程序用来比较两个数组元素并返回指定其关系的值。  要在搜索时，`_lfind_s` 调用例程 `compare` 一次或多次，对每次调用时，传递 `context` 指针和两个数组元素的指针。  `compare` 事务必须比较元素并返回非零 \(这意味着元素完全不同\) 或 0 \(这意味着元素中相同\)。  
  
 `_lfind_s` 类似于 `_lfind`，除了比较函数的`context`指针，和比较函数的参数列表中的参数。  如果搜索的数据结构是对象的一部分，`compare` 函数需要访问对象的成员，`context` 指针可能是有用。  `compare` 函数可以转换无效指针到适当的对象类型，并且访问该对象的成员。  添加`context`参数使得`_lfind_s`更安全，因为附加context可以被用来避免与是使用静态变量关联的重入错误，以使`compare`函数的数据可用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lfind_s`|\<搜索\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
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
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
  **weit found**   
## .NET Framework 等效项  
 <xref:System.Collections.ArrayList.Contains%2A>  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort\_s](../../c-runtime-library/reference/qsort-s.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)