---
title: execution_character_set 杂注
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218626"
---
# <a name="execution_character_set-pragma"></a>execution_character_set 杂注

指定用于字符串和字符文本的执行字符集。 用`u8`前缀标记的文本不需要此指令。

## <a name="syntax"></a>语法

> **#pragma execution_character_set (** "*target*" **)**

### <a name="parameters"></a>参数

*靶*\
指定目标执行字符集。 目前仅支持 "utf-8" 目标执行集。

## <a name="remarks"></a>备注

从 Visual Studio 2015 Update 2 开始, 此编译器指令已过时。 建议`/execution-charset:utf-8`将或`/utf-8`编译器`u8`选项与在包含扩展字符的窄字符和字符串文本上使用前缀一起使用。 有关`u8`前缀的详细信息, 请参阅[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)。 有关编译器选项的详细信息, 请参阅[/execution-charset (设置执行字符集)](../build/reference/execution-charset-set-execution-character-set.md)和[/Utf-8 (将源和可执行字符集设置为 utf-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。

`#pragma execution_character_set("utf-8")`指令指示编译器将源代码中的窄字符和窄字符串文本编码为可执行文件中的 utf-8。 此输出编码独立于所使用的源文件编码。

默认情况下, 编译器使用当前代码页作为执行字符集, 对窄字符和窄字符串进行编码。 这意味着文本中在当前代码页范围之外的 Unicode 或 DBCS 字符将转换为输出中的默认替换字符。 Unicode 和 DBCS 字符被截断为低序位字节。 这并不是您想要的。 您可以通过使用`u8`前缀为源文件中的文本指定 utf-8 编码。 编译器将这些 UTF-8 编码的字符串传递给未更改的输出。 使用 u8 作为前缀的窄字符文本必须在一个字节内, 或在输出时被截断。

默认情况下, Visual Studio 使用当前代码页作为源字符集, 用于解释输出的源代码。 当在中读取文件时, Visual Studio 将根据当前代码页解释它, 除非设置了文件代码页, 或者在文件开头检测到字节顺序标记 (BOM) 或 UTF-16 字符。 因为 UTF-8 不能设置为当前代码页, 所以, 当自动检测遇到编码为 UTF-8 但没有 BOM 的源文件时, Visual Studio 将假定使用当前代码页对它们进行编码。 源文件中的字符超出指定的或自动检测到的代码页的范围, 可能导致编译器警告和错误。

## <a name="see-also"></a>请参阅

[Pragma 指令和\_ \_pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/execution-charset (设置执行字符集)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8（将源和可执行字符集设置为 UTF-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
