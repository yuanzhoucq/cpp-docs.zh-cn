---
title: tchar.h 中的通用文本映射
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
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361347"
---
# <a name="generic-text-mappings-in-tcharh"></a>tchar.h 中的通用文本映射

为了简化代码的传输，国际使用，Microsoft 运行时库为许多数据类型、例程和其他对象提供了特定于 Microsoft 的泛文本映射。 您可以使用这些在 tchar.h 中定义的映射来编写可用于单字节、多字节或 Unicode 字符集的泛型代码，具体取决于使用`#define`语句定义的清单常量。 一般文本映射是与 ANSI 不兼容的 Microsoft 扩展。

通过使用 tchar.h，可以从同一源构建单字节、多字节字符集 （MBCS） 和 Unicode 应用程序。 tchar.h`_tcs`定义宏（具有前缀），这些宏具有正确的前处理器定义，根据需要映射到`str`、`_mbs`或`wcs`函数。 要生成 MBCS，请定义`_MBCS`符号 。 要生成 Unicode，请定义`_UNICODE`符号 。 要生成单字节应用程序，请定义两者（默认值）。 默认情况下，`_UNICODE`为 MFC 应用程序定义。

数据类型`_TCHAR`在 tchar.h 中有条件地定义。 如果为生成`_UNICODE`定义了符号，`_TCHAR`则定义为**wchar_t**。否则，对于单字节和 MBCS 生成，它定义为**字符**。 **（wchar_t，** 基本 Unicode 宽字符数据类型，是 8 位签名**字符**的 16 位对应项 。对于国际应用，请使用以`_tcs`单位而不是字节为单位`_TCHAR`的函数系列。 例如，`_tcsncpy`副本`n``_TCHARs`，而不是`n`字节。

由于某些单字节字符集 （SBCS） 字符串处理函数采用（签名）`char*`参数，因此在定义类型不匹配编译器警告时`_MBCS`会导致错误。 有三种方法可以避免此警告：

1. 在 tchar.h 中使用类型安全内联函数 thunks。 这是默认行为。

1. 通过在命令行上定义`_MB_MAP_DIRECT`，使用 tchar.h 中的直接宏。 如果执行此操作，必须手动匹配类型。 这是最快的方法，但不是类型安全的。

1. 在 tchar.h 中使用类型安全的静态链接库函数 thunks。 为此，在命令行上定义常量 `_NO_INLINING`。 这是最慢的方法，但是最能确保类型安全。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>用于一般文本映射的预处理器指令

|• 定义|编译的版本|示例|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode（宽字符）|`_tcsrev` 映射到 `_wcsrev`|
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|
|无（默认值既未`_UNICODE`定义，`_MBCS`也未定义）|SBCS (ASCII)|`_tcsrev` 映射到 `strrev`|

例如，在 tchar.h`_tcsrev`中定义的泛文本函数`_mbsrev`映射到在程序中`_MBCS`定义时，或者如果`_wcsrev`定义了`_UNICODE`。 否则，`_tcsrev` 将映射到 `strrev`。 其他数据类型映射在 tchar.h 中提供，以方便编程，但`_TCHAR`最有用。

### <a name="generic-text-data-type-mappings"></a>一般文本数据类型映射

|通用文本<br /> 数据类型名称|_UNICODE&<br /> 未定义_MBCS|_MBCS<br /> 已定义|_UNICODE<br /> 已定义|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**Int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**signed char**|**signed char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` 或 `_TEXT`|无效果（由预处理器删除）|无效果（由预处理器删除）|`L`（将以下字符或字符串转换为其 Unicode 对应字符）|

有关例程、变量和其他对象的泛文本映射的列表，请参阅运行时库参考中的[通用文本映射](../c-runtime-library/generic-text-mappings.md)。

> [!NOTE]
> 请勿将具有`str`Unicode 字符串的函数系列使用，该字符串可能包含嵌入的 null 字节。 同样，不要将`wcs`函数系列与 MBCS（或 SBCS） 字符串一起使用。

以下代码片段说明了用于映射到 MBCS、Unicode 和 SBCS 模型的 `_TCHAR` 和 `_tcsrev` 的使用方法。

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

如果`_MBCS`已定义，预处理器将此片段映射到此代码：

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

如果`_UNICODE`已定义，预处理器将此片段映射到此代码：

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

如果未定义`_MBCS`，`_UNICODE`则预处理器将片段映射到单字节 ASCII 代码，如下所示：

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此，您可以编写、维护和编译单源代码文件，以便使用特定于三种字符集中的任何一种的例程运行。

## <a name="see-also"></a>另请参阅

[文本和字符串](../text/text-and-strings-in-visual-cpp.md)<br/>
[使用 TCHAR。H 数据类型具有_MBCS代码](../text/using-tchar-h-data-types-with-mbcs-code.md)
