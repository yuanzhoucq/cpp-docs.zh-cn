---
title: 字符集
ms.date: 05/06/2019
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 92d60e3383abd7e3b3fa2d689958cf02a9b91e75
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222522"
---
# <a name="character-sets"></a>字符集

C++ 程序的文本存储在使用特定字符编码的源文件中。 C++ 标准指定源文件的基本源字符集和已编译文件的基本执行字符集。 MicrosoftC++编译器 (MSVC) 允许一组额外的区域设置特定字符在源文件中使用和已编译的文件。

## <a name="character-sets"></a>字符集

C++ 标准指定可用于源文件的 *基本源字符集* 。 若要表示这组字符之外的字符，可以通过使用 *通用字符名称*指定其他字符。 编译后， *基本执行字符集* 和 *基本执行宽字符集* 表示可以出现在程序中的字符和字符串。 MSVC 实现允许在源代码和编译的代码中的其他字符。

### <a name="basic-source-character-set"></a>基本源字符集

*基本源字符集* 由可用于源文件的 96 个字符组成。 这组字符包括空白字符、水平选项卡、垂直选项卡、换页符和换行控制字符以及这一组图形字符：

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft 专用**

MSVC 包括`$`字符作为基本源字符集的成员。 MSVC 还允许一组额外的字符要在源代码文件中使用基于文件编码。 默认情况下，Visual Studio 通过使用默认代码页存储源文件。 当使用特定于区域设置代码页或 Unicode 代码页保存源文件时，MSVC，可在源代码中使用该代码页的字符的任何基本源字符集中未明确允许的控制代码除外设置。 例如，如果你使用日语代码页保存文件，则可以在注释、标识符或字符串中放置日语字符。 MSVC 不允许不能转换为有效多字节字符或 Unicode 码位的字符序列。 并非所有允许的字符均可显示在标识符中，具体取决于编译器选项。 有关详细信息，请参阅 [Identifiers](../cpp/identifiers-cpp.md)。

**结束 Microsoft 专用**

### <a name="universal-character-names"></a>通用字符名称

由于 C++ 程序可使用的字符要比在基本源字符集中指定的字符要多得多，所以可以通过使用 *通用字符名称*以可移植的方式指定这些字符。 通用字符名称由表示 Unicode 码位的字符序列组成。  采用两种形式。 使用 `\UNNNNNNNN` 表示形式为 U+NNNNNNNN 的 Unicode 码位，其中 NNNNNNNN 是八位的十六进制码位数字。 使用四位的 `\uNNNN` 表示形式为 U+0000NNNN 的 Unicode 码位。

通用字符名称可用于标识符、字符串和字符文本中。 通用字符名称不能用于表示范围 0xD800-0xDFFF 之内的代理项码位。 而应使用所需的码位；编译器会自动生成任何必需的代理项。 其他限制适用于可在标识符中使用的通用字符名称。 有关详细信息，请参阅 [Identifiers](../cpp/identifiers-cpp.md) 和 [String and Character Literals](../cpp/string-and-character-literals-cpp.md)。

**Microsoft 专用**

MicrosoftC++编译器将通用字符名称形式和文本形式中的字符互换。 例如，你可以声明一个使用通用字符名称形式的标识符，并以文本形式使用它：

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Windows 剪贴板上的扩展字符的格式特定于应用程序区域设置。 从另一个应用程序剪切这些字符并将其粘贴到你的代码中可能会引入意外的字符编码。 这可能会导致在你的代码中出现原因不可见的分析错误。 我们建议你在粘贴扩展的字符之前将你的源文件编码设置为 Unicode 代码页。 我们还建议你使用 IME 或字符映射应用生成扩展的字符。

**结束 Microsoft 专用**

### <a name="basic-execution-character-set"></a>基本执行字符集

*基本执行字符集* 和 *基本执行宽字符集* 的构成包括基本源字符集中的所有字符和用于表示警报、退格符、回车符和 null 字符的控制字符。 *执行字符集* 和 *执行宽字符集* 是基本集的超集。 它们包括基本原字符集之外的由实现定义的源字符。 执行字符集具有特定于区域设置的表示形式。