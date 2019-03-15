---
title: Tchar.h 中的一般文本映射
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: 779702aa33e2aa24bf5a380bd8435745cc0aadbd
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822634"
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar.h 中的一般文本映射

若要简化的全球范围内使用的代码的传输，Microsoft 运行库提供特定于 Microsoft 的一般文本映射的许多数据类型、 例程和其他对象。 可以使用这些映射，tchar.h，能够编写泛型可以为单字节，多字节，编译的代码中定义或设置的 Unicode 字符，具体取决于您通过使用定义的清单常量`#define`语句。 一般文本映射是与 ANSI 不兼容的 Microsoft 扩展。

使用 tchar.h，可以生成单字节、 多字节字符集 (MBCS) 和 Unicode 应用程序从相同的源。 Tchar.h 定义宏 (其中包含前缀`_tcs`)，使用正确的预处理器定义的它将映射到`str`， `_mbs`，或`wcs`函数，根据需要。 若要生成 MBCS，请定义符号`_MBCS`。 若要生成 Unicode，请定义符号`_UNICODE`。 若要生成的单字节应用程序，定义都不 （默认值）。 默认情况下，`_UNICODE`为 MFC 应用程序定义。

`_TCHAR`有条件地在 tchar.h 中定义数据类型。 如果符号`_UNICODE`为您的生成定义`_TCHAR`指**wchar_t**; 否则为对于单字节和 MBCS 版本，它被定义为**char**。 (**wchar_t**，基本的 Unicode 宽字符数据类型，是为 8 位带符号的 16 位对应**char**。)针对国际性应用，使用`_tcs`系列函数，在操作`_TCHAR`单位，而非字节。 例如，`_tcsncpy`副本`n` `_TCHARs`，而不`n`字节。

因为某些单字节字符集 (SBCS) 字符串处理函数采用 （带符号）`char*`参数，类型不匹配编译器警告结果时`_MBCS`定义。 有三种方法，以避免出现此警告：

1. 使用 tchar.h 中类型安全的内联函数 thunk。 这是默认行为。

1. 使用 tchar.h 中的直接的宏，通过定义`_MB_MAP_DIRECT`命令行上。 如果执行此操作，必须手动匹配类型。 这是最快方法，但不是类型安全。

1. 使用 tchar.h 中类型安全的静态链接的库函数 thunk。 为此，在命令行上定义常量 `_NO_INLINING`。 这是最慢的方法，但是最能确保类型安全。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>用于一般文本映射的预处理器指令

|# 定义|编译的版本|示例|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode（宽字符）|`_tcsrev` 映射到 `_wcsrev`|
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|
|None (默认具有都`_UNICODE`也不`_MBCS`定义)|SBCS (ASCII)|`_tcsrev` 映射到 `strrev`|

例如，一般文本函数`_tcsrev`，在 tchar.h 中定义映射到`_mbsrev`如果你定义`_MBCS`在应用程序中，或设置为`_wcsrev`如果定义了`_UNICODE`。 否则，`_tcsrev` 将映射到 `strrev`。 其他数据类型映射在 tchar.h 中提供为了编程方便，但`_TCHAR`最为有用。

### <a name="generic-text-data-type-mappings"></a>一般文本数据类型映射

|Generic-Text<br /> 数据类型名称|_UNICODE （&AMP; A)<br /> 未定义 _MBCS|_MBCS<br /> 已定义|_UNICODE<br /> 已定义|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**有符号的字符**|**有符号的字符**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` 或 `_TEXT`|无效果（由预处理器删除）|无效果（由预处理器删除）|`L` （将以下字符或字符串转换为其 Unicode 对应）|

有关一般文本映射的例程、 变量和其他对象的列表，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)运行时库参考中。

> [!NOTE]
>  不要使用`str`系列函数处理 Unicode 字符串，其中可能包含嵌入的 null 字节。 同样，不要使用`wcs`系列函数使用 MBCS （或 SBCS） 的字符串。

以下代码片段说明了用于映射到 MBCS、Unicode 和 SBCS 模型的 `_TCHAR` 和 `_tcsrev` 的使用方法。

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

如果`_MBCS`已定义，则预处理器将此片段映射到此代码：

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

如果`_UNICODE`已定义，则预处理器将此片段映射到此代码：

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

如果既没有`_MBCS`也不`_UNICODE`已定义，则预处理器将片段映射到单字节 ASCII 代码，按如下所示：

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此，可以编写、 维护和编译单个源代码文件以特定于任何字符集的三种的例程一起运行。

## <a name="see-also"></a>请参阅

[文本和字符串](../text/text-and-strings-in-visual-cpp.md)<br/>
[将 TCHAR.H 数据类型用于 _MBCS 代码](../text/using-tchar-h-data-types-with-mbcs-code.md)
