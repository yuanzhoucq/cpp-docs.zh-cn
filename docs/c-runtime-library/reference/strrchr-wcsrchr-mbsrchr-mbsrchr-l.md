---
title: "strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
dev_langs: C++
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a7f498dc526d6989e18aaf8aea916ad9fc602cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr、wcsrchr、_mbsrchr、_mbsrchr_l
扫描字符串以查找某个字符的末次出现位置。  
  
> [!IMPORTANT]
>  `_mbsrchr` 和 `_mbsrchr_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
char *strrchr(  
   const char *str,  
   int c   
); // C only  
char *strrchr(  
   char *str,  
   int c   
); // C++ only  
const char *strrchr(  
   const char *str,  
   int c   
); // C++ only  
wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcsrchr(  
   wchar_t *str,  
   wchar_t c   
); // C++ only  
const wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C++ only  
unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbsrchr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only  
unsigned char *_mbsrchr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 要搜索的 null 终止的字符串。  
  
 `c`  
 要查找的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回指向 `str` 中的 `c` 末次出现位置的指针；如果找不到 `c`，则返回 `NULL`。  
  
## <a name="remarks"></a>备注  
 `strrchr` 函数查找 `str` 中的 `c`（已转换为 `char`）末次出现位置。 搜索包括终止 null 字符。  
  
 `wcsrchr` 和 `_mbsrchr` 分别是 `strrchr` 的宽字符及多字节字符版本。 `wcsrchr` 的参数和返回值是宽字符字符串；而 `_mbsrchr` 的则是多字节字符字符串。  
  
 在 C 中，这些函数采用第一个参数的一个 `const` 指针。 在 C++ 中，有两个重载可用。 采用指向 `const` 的指针的重载返回指向 `const` 的指针；采用指向非`const` 的版本的指针返回指向非`const` 的指针。 宏`_CRT_CONST_CORRECT_OVERLOADS`如果这两个定义`const`和非-`const`提供了这些函数的版本。 如果需要非`const`这两个 c + + 重载，行为定义符号`_CONST_RETURN`。  
  
 `_mbsrchr` 会验证其参数。 如果 `str` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 `errno` 设置为 `EINVAL`，并且 `_mbsrchr` 将返回 0。 `strrchr` 和 `wcsrchr` 不会验证其参数。 否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|  
|**不适用**|**不适用**|`_mbsrchr_l`|**不适用**|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`strrchr`|\<string.h>|  
|`wcsrchr`|\<string.h> 或 \<wchar.h>|  
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|  
  
 有关兼容性的更多信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 有关使用 `strrchr` 的示例，请参阅 [strchr](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)。  
  
## <a name="see-also"></a>请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strchr、wcschr、_mbschr、_mbschr_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strcspn、wcscspn、_mbscspn、_mbscspn_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)