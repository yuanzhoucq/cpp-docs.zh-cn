---
title: _emit Pseudoinstruction
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: 8be250aadf20dc4a7dee6a0b565ece21840339d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169469"
---
# <a name="_emit-pseudoinstruction"></a>_emit Pseudoinstruction

**Microsoft 专用**

**_Emit** pseudoinstruction 定义当前文本段当前位置中的一个字节。 **_Emit** PSEUDOINSTRUCTION 与 MASM 的[DB](../../assembler/masm/db.md)指令类似。

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
> 如果 `_emit` 生成了修改寄存器的指令，并且您在编译应用程序时进行了优化，则编译器无法确定受到影响的寄存器。 例如，如果 `_emit` 生成了修改**rax** register 的指令，则编译器不知道**rax**已更改。 在内联汇编程序代码执行后，编译器随后可能会对该寄存器中的值做出错误假设。 因此，在应用程序运行时，它可能展示出不可预知的行为。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
