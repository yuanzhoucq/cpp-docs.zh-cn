---
title: Tchar.h 中的一般文本映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7ed29b03a37c9b911a954192152115b1458fd94
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar.h 中的一般文本映射
若要简化的代码的全球范围内使用，传输[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]运行时库提供[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-特定一般文本映射的多种数据类型、 例程和其他对象。 你可以使用这些映射，Tchar.h，编写可以为单字节，多字节，编译的泛型代码中定义或[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]字符集，具体取决于你使用定义的清单常量`#define`语句。 一般文本映射是[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]不扩展[!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)]兼容。  
  
 可以通过使用 Tchar.h，生成单字节，多字节字符集 (MBCS)，和[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]从相同的源的应用程序。 Tchar.h 定义宏 (其中包含前缀`_tcs`)，正确的预处理器定义，将映射到`str`， `_mbs`，或`wcs`函数，根据需要。 若要生成 MBCS，请定义符号`_MBCS`。 若要生成[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]，定义符号`_UNICODE`。 若要生成单字节应用程序，定义任何 （默认设置）。 默认情况下，`_MBCS`为 MFC 应用程序定义。  
  
 `_TCHAR`有条件地在 Tchar.h 中定义的数据类型。 如果符号`_UNICODE`为你的生成定义`_TCHAR`定义为`wchar_t`; 否则为单字节和 MBCS 生成，则它将定义为`char`。 (`wchar_t`，基本 Unicode 宽字符数据类型，是 8 位带符号的 16 位对应`char`。)国际应用程序，对于使用`_tcs`函数，在运行系列`_TCHAR`单位、 非字节。 例如，`_tcsncpy`副本`n` `_TCHARs`，而不`n`字节。  
  
 因为某些单字节字符集 (SBCS) 字符串处理函数采用 （带符号）`char*`参数、 类型不匹配编译器警告结果时`_MBCS`定义。 有三种方法，以避免此警告：  
  
1.  使用 Tchar.h 中的类型安全内联函数 thunk。 这是默认行为。  
  
2.  使用 Tchar.h 中的直接宏，通过定义`_MB_MAP_DIRECT`命令行上。 如果执行此操作，必须手动匹配类型。 这是最快的方法，但不是类型安全。  
  
3.  使用 Tchar.h 中的类型安全静态链接的库函数 thunk。 为此，在命令行上定义常量 `_NO_INLINING`。 这是最慢的方法，但是最能确保类型安全。  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>用于一般文本映射的预处理器指令  
  
|# 定义|编译的版本|示例|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] （宽字符）|`_tcsrev` 映射到 `_wcsrev`|  
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|  
|无 (默认值已不`_UNICODE`也不`_MBCS`定义)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev` 映射到 `strrev`|  
  
 例如，一般文本函数`_tcsrev`，Tchar.h 中定义映射到`_mbsrev`如果定义`_MBCS`在程序中，或设置为`_wcsrev`如果定义`_UNICODE`。 否则，`_tcsrev` 将映射到 `strrev`。 其他数据类型映射 Tchar.h 中还提供便于进行编程，但`_TCHAR`是最有用的。  
  
### <a name="generic-text-data-type-mappings"></a>一般文本数据类型映射  
  
|一般文本<br /><br /> 数据类型名称|_UNICODE （&AMP; A)<br /><br /> 未定义 _MBCS|_MBCS<br /><br /> 已定义|_UNICODE<br /><br /> 已定义|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|无效果（由预处理器删除）|无效果（由预处理器删除）|`L` (将以下字符或字符串转换其[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]对应项)|  
  
 一般文本映射的例程、 变量和其他对象的列表，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)运行时库参考中。  
  
> [!NOTE]
>  不要使用`str`系列函数使用 Unicode 字符串，其可能包含嵌入的 null 字节。 同样，不要使用`wcs`系列具有 MBCS （或 SBCS） 字符串的函数。  
  
 下面的代码段演示如何使用`_TCHAR`和`_tcsrev`映射到 MBCS， [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]，和 SBCS 模型。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果`_MBCS`已定义，则预处理器对此代码中映射此片段：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果`_UNICODE`已定义，则预处理器对此代码中映射此片段：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果既没有`_MBCS`也不`_UNICODE`已定义，则预处理器将片段映射到单字节[!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)]代码，，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此，你可以编写、 维护和编译的源代码文件以运行与特定于任何字符集三种类型的例程。  
  
## <a name="see-also"></a>请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [将 TCHAR.H 数据类型用于 _MBCS 代码](../text/using-tchar-h-data-types-with-mbcs-code.md)