---
title: / DISASM |Microsoft 文档
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /disasm
dev_langs:
- C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89b0784ff10e7d9521351e01d8907c963c9304fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370366"
---
# <a name="disasm"></a>/DISASM

打印 DUMPBIN 输出中的代码段的反汇编。

## <a name="syntax"></a>语法

> **/ DISASM**{**:**\[**字节**|**NOBYTES**]}  

### <a name="arguments"></a>自变量

**BYTES**  
反汇编输出中包括的解释型操作码和自变量一起的指令字节。 这是默认选项。

**NOBYTES**  
不反汇编输出中包括的指令字节。

## <a name="remarks"></a>备注

**/DISASM**选项显示代码段的反汇编文件中。 如果在文件中出现，它使用调试符号。

**/ DISASM**应仅使用本机、 不受管理，映像上。 托管代码的等效工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可由生成的文件上使用[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)  
