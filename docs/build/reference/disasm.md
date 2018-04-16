---
title: /DISASM | Microsoft Docs
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d448b92c3436f3d2875bd8d9b8e0af6a7149e065
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2018
---
# <a name="disasm"></a>/DISASM

打印 DUMPBIN 输出中的代码段的反汇编。

## <a name="syntax"></a>语法

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}  

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
