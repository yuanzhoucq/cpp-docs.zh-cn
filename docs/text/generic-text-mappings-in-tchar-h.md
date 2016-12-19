---
title: "Tchar.h 中的一般文本映射 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""tchar.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符集 [C++], 一般文本映射"
  - "一般文本映射 [C++]"
  - "映射一般文本"
  - "映射 [C++], TCHAR.H"
  - "MBCS [C++], 一般文本映射"
  - "TCHAR.H 数据类型, 映射"
  - "Unicode [C++], 一般文本映射"
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
caps.latest.revision: 12
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Tchar.h 中的一般文本映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为简化代码的传输，便于在国际上使用，[!INCLUDE[TLA#tla_ms](../Token/TLA%23tla_ms_md.md)] 运行库为许多数据类型、例程和其他对象提供 [!INCLUDE[TLA#tla_ms](../Token/TLA%23tla_ms_md.md)] 特有的一般文本映射。  您可以使用 Tchar.h 中定义的这些映射，根据使用 `#define` 语句定义的清单常数，编写可以为单字节、多字节或 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 字符集编译的泛型代码。  一般文本映射是与 [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] 不兼容的 [!INCLUDE[TLA#tla_ms](../Token/TLA%23tla_ms_md.md)] 扩展。  
  
 使用 Tchar.h，可以从同一个源生成单字节应用程序、多字节字符集 \(MBCS\) 应用程序和 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 应用程序。  Tchar.h 定义（以 `_tcs` 为前缀的）宏，这些宏根据正确的预处理器定义映射到适当的 `str`、`_mbs` 或 `wcs` 函数。  若要生成 MBCS，请定义 `_MBCS` 符号。  若要生成 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)]，请定义 `_UNICODE` 符号。  若要生成单字节应用程序，请不进行任何定义（默认）。  默认情况下，为 MFC 应用程序定义的是 `_MBCS`。  
  
 在 Tchar.h 中根据条件定义 `_TCHAR` 数据类型。  如果为您的生成定义了 `_UNICODE` 符号，则 `_TCHAR` 被定义为 `wchar_t`；否则，对于单字节和 MBCS 生成，它被定义为 `char`。（`wchar_t` 是基本的 Unicode 宽字符数据类型，它是 8 位有符号 `char` 的 16 位对等项。）对于国际应用程序，使用以 `_TCHAR`（而非字节）为单位进行运算的 `_tcs` 函数族。  例如，`_tcsncpy` 复制 `n` 个 `_TCHARs`，而不是 `n` 个字节。  
  
 由于某些单字节字符集 \(SBCS\) 字符串处理函数采用（有符号的）`char*` 参数，因此定义 `_MBCS` 时，编译器会发出类型不匹配的警告。  可通过三种方法来避免此警告：  
  
1.  在 Tchar.h 中使用类型安全的内联函数 thunk。  这是默认行为。  
  
2.  通过在命令行上定义 `_MB_MAP_DIRECT`，在 Tchar.h 中使用直接宏。  如果这样做，必须手动匹配类型。  这是最快的方法，但不是类型安全的方法。  
  
3.  在 Tchar.h 中使用类型安全静态链接库函数 thunk。  为此，请在命令行上定义 `_NO_INLINING` 常量。  这是最慢的方法，但却是类型安全性最高的方法。  
  
### 一般文本映射的预处理器指令  
  
|\# define|编译版本|示例|  
|---------------|----------|--------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)]（宽字符）|`_tcsrev` 映射到 `_wcsrev`|  
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|  
|无（默认值既未定义 `_UNICODE` 也未定义 `_MBCS`）|SBCS \([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)]\)|`_tcsrev` 映射到 `strrev`|  
  
 例如，如果在程序中定义了 `_MBCS`，则 Tchar.h 中定义的一般文本函数 `_tcsrev` 映射到 `_mbsrev`。或者，如果定义了 `_UNICODE`，则映射到 `_wcsrev`。  否则，`_tcsrev` 映射到 `strrev`。  在 Tchar.h 中还提供了其他数据类型映射以方便编程，但 `_TCHAR` 是最有用的。  
  
### 一般文本数据类型映射  
  
|一般文本<br /><br /> 数据类型名称|UNICODE &<br /><br /> \_MBCS 未定义|\_MBCS<br /><br /> 已定义|\_UNICODE<br /><br /> 已定义|  
|---------------------|------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|无效（由预处理器移除）|无效（由预处理器移除）|`L`（将后面的字符或字符串转换成相应的 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 形式）|  
  
 有关例程、变量和其他对象的一般文本映射的列表，请参见“运行库参考”中的[一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
> [!NOTE]
>  Unicode 字符串有可能包含嵌入 null 字节，所以不要在 Unicode 字符串中使用 `str` 函数族。  同样，不要在 MBCS（或 SBCS）字符串中使用 `wcs` 函数族。  
  
 下列代码片段阐释了用于映射到 MBCS、[!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 和 SBCS 模型的 `_TCHAR` 和 `_tcsrev` 的用法。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果已定义 `_MBCS`，则预处理器将此片段映射到以下代码：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果已定义 `_UNICODE`，则预处理器将此片段映射到以下代码：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果既未定义 `_MBCS` 也未定义 `_UNICODE`，则预处理器将此片段映射到单字节 [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] 代码，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此，您可以编写、维护和编译与三种字符集中任何一种的特定例程一起运行的单个源代码文件。  
  
## 请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [将 TCHAR.H 数据类型用于 \_MBCS 代码](../text/using-tchar-h-data-types-with-mbcs-code.md)