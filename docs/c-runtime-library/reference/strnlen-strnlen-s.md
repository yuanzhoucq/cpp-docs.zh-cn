---
title: strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: be13a67d51b0296d91355c970e5e37ad227812ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919255"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

使用当前区域设置或已传入的一个区域设置获取字符串的长度。 这些是 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 的更加安全的版本。

> [!IMPORTANT]
> **_mbsnlen**、 **_mbsnlen_l**、 **_mbstrnlen**和 **_mbstrnlen_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串*<br/>
以 Null 结尾的字符串。

*numberOfElements*<br/>
字符串缓冲区的大小。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

这些函数将返回字符串中的字符数，不包括以 null 结尾的字符。 如果字符串的第一个*numberOfElements*字节内没有空终止符（对于**wcsnlen**，则为宽字符），则返回*numberOfElements* ，以指示错误条件;以 null 结尾的字符串的长度严格小于*numberOfElements*。

如果字符串包含无效的多字节字符，则 **_mbstrnlen**和 **_mbstrnlen_l**返回-1。

## <a name="remarks"></a>备注

> [!NOTE]
> **strnlen**不是**strlen**的替代;**strnlen**仅用于计算已知大小的缓冲区中传入的不受信任数据的大小，例如网络数据包。 **strnlen**计算长度，但如果字符串未终止，则不会遍历缓冲区的末尾。 对于其他情况，请使用**strlen**。 （这同样适用于**wcsnlen**、 **_mbsnlen**和 **_mbstrnlen**。）

其中每个函数均返回*str*中的字符数，不包括终止 null 字符。 但是， **strnlen**和**strnlen_s**会将字符串解释为单字节字符字符串，因此，即使字符串包含多字节字符，返回值也始终等于字节数。 **wcsnlen**和**wcsnlen_s**分别是**strnlen**和**strnlen_s**的宽字符版本;**wcsnlen**和**wcsnlen_s**的参数是宽字符字符串且字符计数以宽字符为单位。 否则， **wcsnlen**和**strnlen**的行为方式与**strnlen_s**和**wcsnlen_s**相同。

**strnlen**、 **wcsnlen**和 **_mbsnlen**不会验证其参数。 如果*str*为**NULL**，则会发生访问冲突。

**strnlen_s**和**wcsnlen_s**验证其参数。 如果*str*为**NULL**，则函数返回0。

**_mbstrnlen**还会验证其参数。 如果*str*为**NULL**，或者如果*numberOfElements*大于**INT_MAX**， **_Mbstrnlen**将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续， **_mbstrnlen**将**Errno**设置为**EINVAL** ，并返回-1。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**和 **_mbstrnlen**返回多字节字符字符串中的多字节字符数。 **_mbsnlen**根据当前使用的多字节代码页或已传入的区域设置来识别多字节字符序列;它不会测试多字节字符的有效性。 **_mbstrnlen**测试多字节字符的有效性并识别多字节字符序列。 如果传递到 **_mbstrnlen**的字符串包含无效的多字节字符，则将**Errno**设置为**eilseq 且**。

输出值受区域设置的**LC_CTYPE**类别设置的设置的影响;有关详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 这些函数的版本相同，不同之处在于没有 **_l**后缀的函数会将当前区域设置用于与区域设置相关的行为，并使用传入的区域设置参数 **_l**后缀。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strnlen**、 **strnlen_s**|\<string.h>|
|**wcsnlen**、 **wcsnlen_s**|\<string.h> 或 \<wchar.h>|
|**_mbsnlen**， **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**， **_mbstrnlen_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
