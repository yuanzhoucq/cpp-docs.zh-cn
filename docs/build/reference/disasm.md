---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822530"
---
# <a name="disasm"></a>/DISASM

打印 DUMPBIN 输出中的代码段的反汇编。

## <a name="syntax"></a>语法

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>自变量

**BYTES**<br/>
反汇编输出中包括与已解释的操作码和自变量的指令字节。 这是默认选项。

**NOBYTES**<br/>
不反汇编输出中包括的指令的字节数。

## <a name="remarks"></a>备注

**/DISASM**选项显示代码段的反汇编文件中。 如果它们存在的文件中，它使用调试符号。

**/DISASM**仅用于本机、 未托管的映像上。 托管代码的等效工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

仅[/HEADERS](headers.md) DUMPBIN 选项是可用于生成的文件[/GL （全程序优化）](gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
