---
title: _emit pseudoinstruction |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 569e3a078109e66df7dcf5cbf314817ce0786899
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061919"
---
# <a name="emit-pseudoinstruction"></a>_emit Pseudoinstruction

**Microsoft 专用**

**_Emit** pseudoinstruction 定义中当前文本段落的当前位置处的一个字节。 **_Emit**伪命令类似于[DB](../../assembler/masm/db.md) MASM 指令。

以下片段将字节 0x4A、0x43 和 0x4B 放入代码中：

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> 如果 `_emit` 生成了修改寄存器的指令，并且您在编译应用程序时进行了优化，则编译器无法确定受到影响的寄存器。 例如，如果`_emit`生成的指令的修改**rax**寄存器，编译器将不知道**rax**已更改。 在内联汇编程序代码执行后，编译器随后可能会对该寄存器中的值做出错误假设。 因此，在应用程序运行时，它可能展示出不可预知的行为。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>