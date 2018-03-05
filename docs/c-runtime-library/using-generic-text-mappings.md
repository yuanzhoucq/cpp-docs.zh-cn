---
title: "使用一般文本映射 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _UNICODE
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0049643ef7a3695eef8c3271e22586b5c7454d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-generic-text-mappings"></a>使用一般文本映射
**Microsoft 专用**  
  
 为了简化各种国际市场的代码开发，Microsoft 运行时库为许多数据类型、例程和其他对象提供了 Microsoft 专用的“一般文本”映射。 这些映射在 TCHAR.H 中进行定义。 可以使用这些名称映射来编写可编译全部三种字符集（ASCII (SBCS)、MBCS 或 Unicode）的通用代码：具体取决于使用 `#define` 语句定义的清单常量。 一般文本映射是与 ANSI 不兼容的 Microsoft 扩展。  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>用于一般文本映射的预处理器指令  
  
|#define|编译的版本|示例|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Unicode（宽字符）|`_tcsrev` 映射到 `_wcsrev`|  
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|  
|无（默认值：未定义 `_UNICODE` 和 `_MBCS`）|SBCS (ASCII)|`_tcsrev` 映射到 `strrev`|  
  
 例如，如果已在程序中定义了 `MBCS`，则在 TCHAR.H 中定义的一般文本函数 `_tcsrev` 映射到 `mbsrev`，如果已定义了 `_UNICODE`，则将映射到 `_wcsrev`。 否则，`_tcsrev` 将映射到 `strrev`。  
  
 如果已定义了 `_MBCS`，则仍在 TCHAR.H 中定义的一般文本数据类型 `_TCHAR` 将映射到类型 `char`，如果定义了 `_UNICODE`，则映射到类型 `wchar_t`，如果未定义任何常量，则映射到 `char`。 TCHAR.H 中提供了其他数据类型映射，可方便地用于编程，但 `_TCHAR` 是最有用的类型。  
  
### <a name="generic-text-data-type-mappings"></a>一般文本数据类型映射  
  
|一般文本数据类型名称|SBCS（未定义的 _UNICODE 和 _MBCS）|已定义 _MBCS|已定义 _UNICODE|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|无效果（由预处理器删除）|无效果（由预处理器删除）|`L`（将以下字符或字符串转换为其 Unicode 对应项）|  
  
 有关例程、变量和其他对象的一般文本映射的完整列表，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
 以下代码片段说明了用于映射到 MBCS、Unicode 和 SBCS 模型的 `_TCHAR` 和 `_tcsrev` 的使用方法。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果定义了 `MBCS`，则预处理器将前面的片段映射到以下代码：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果定义了 `_UNICODE`，则预处理器将同一片段映射到以下代码：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果 `_MBCS` 和 `_UNICODE` 均未定义，则预处理器将片段映射到单字节 ASCII 代码，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此，可以编写、维护和编译单个源代码文件，来与特定于三种字符集中任何一种的例程一起运行。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [一般文本映射](../c-runtime-library/generic-text-mappings.md)   
 [数据类型映射](../c-runtime-library/data-type-mappings.md)   
 [常量和全局变量映射](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [例程映射](../c-runtime-library/routine-mappings.md)   
 [示例一般文本程序](../c-runtime-library/a-sample-generic-text-program.md)