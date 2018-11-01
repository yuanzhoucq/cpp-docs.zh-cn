---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 77f6f05029ec4480afb2180eab0bb57838d643a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462941"
---
# <a name="disasm"></a>/DISASM

打印 DUMPBIN 输出中的代码段的反汇编。

## <a name="syntax"></a>语法

> **/DISASM**{**:**\[**字节**|**NOBYTES**]}

### <a name="arguments"></a>自变量

**BYTES**<br/>
反汇编输出中包括与已解释的操作码和自变量的指令字节。 这是默认选项。

**NOBYTES**<br/>
不反汇编输出中包括的指令的字节数。

## <a name="remarks"></a>备注

**/DISASM**选项显示代码段的反汇编文件中。 如果它们存在的文件中，它使用调试符号。

**/DISASM**仅用于本机、 未托管的映像上。 托管代码的等效工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可用于生成的文件[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)
