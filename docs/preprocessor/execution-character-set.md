---
title: execution_character_set |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b81832ba31fc8ef36510ce4f35c9fb1a5f3426b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075016"
---
# <a name="executioncharacterset"></a>execution_character_set

指定执行字符集，用于字符串和字符文本。 此指令则不需要使用 u8 前缀标记的文字。

## <a name="syntax"></a>语法

```
#pragma execution_character_set("target")
```

### <a name="parameters"></a>参数

*target*<br/>
指定目标执行字符集。 目前唯一的目标执行设置支持为"utf-8"。

## <a name="remarks"></a>备注

此编译器指令是在 Visual Studio 2015 Update 2 开始已过时。 我们建议你使用`/execution-charset:utf-8`或`/utf-8`编译器选项一起使用`u8`上包含扩展的字符的窄字符和字符串文本的前缀。 有关详细信息`u8`前缀，请参阅[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)。 有关编译器选项的详细信息，请参阅[/execution-charset （设置执行字符集）](../build/reference/execution-charset-set-execution-character-set.md)并[/utf-8 （设置源和可执行文件为 utf-8 字符集）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。

`#pragma execution_character_set("utf-8")`指令指示编译器将可执行文件中编码为 utf-8 窄字符并在源代码中的窄字符串文本。 此输出编码是独立于使用的源文件编码。

默认情况下，编译器将窄字符和窄字符串编码为执行字符集使用当前代码页。 这意味着，Unicode 或 DBCS 字符文本中将当前代码页的范围外的转换为默认替换字符在输出中。 Unicode 和 DBCS 字符被截断为其低序位字节。 这是几乎可以肯定并非您的预期。 您可以指定 utf-8 编码的源代码文件中的文本，方法是使用`u8`前缀。 编译器将这些 utf-8 编码的字符串传递给保持不变的输出。 通过使用 u8 为前缀的窄字符文本必须能够装入一个字节，或它们将在输出被截断。

默认情况下，Visual Studio 作为源字符集，用于解释源代码为输出使用当前代码页。 在读取文件时，Visual Studio 将其解释根据当前代码页设置的文件代码页，除非或者文件的开始处检测到一个字节顺序标记 (BOM) 或 UTF 16 个字符。 因为 utf-8 不能设置为当前代码页，自动检测遇到为不带 BOM 的 utf-8 编码的源文件时，Visual Studio 将假定它们使用的当前代码页编码。 源代码文件中的字符，超出范围的指定或自动检测到的代码页可能会导致编译器警告和错误。

## <a name="see-also"></a>请参阅

[Pragma 指令和\_\_杂注关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/execution-charset （设置执行字符集）](../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)