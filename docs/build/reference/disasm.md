---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927720"
---
# <a name="disasm"></a>/DISASM

在 DUMPBIN 输出中打印代码部分的反汇编。

## <a name="syntax"></a>语法

> **/DISASM**{ **：** \[BYTESNOBYTES|]}

### <a name="arguments"></a>自变量

**BYTES**<br/>
包含指令字节以及反汇编输出中解释的操作码和参数。 这是默认选项。

**NOBYTES**<br/>
不会在反汇编输出中包含指令字节。

## <a name="remarks"></a>备注

**/DISASM**选项显示文件中代码段的反汇编。 如果文件中存在调试符号，则使用调试符号。

**/DISASM**应仅用于本机、非托管映像。 托管代码的等效工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

只有[/HEADERS](headers.md) DUMPBIN 选项可用于由[/gl （全程序优化）](gl-whole-program-optimization.md)编译器选项生成的文件。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
