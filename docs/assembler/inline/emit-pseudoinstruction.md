---
title: _emit pseudoinstruction |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7ad75f4abf2e86cb08ba646e50e9390650993d05
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050693"
---
# <a name="emit-pseudoinstruction"></a>_emit Pseudoinstruction
## <a name="microsoft-specific"></a>Microsoft 专用  
 **_Emit** pseudoinstruction 定义在当前的文本段中的当前位置处的一个字节。 **_Emit** pseudoinstruction 类似于[DB](../../assembler/masm/db.md) MASM 指令。  
  
 以下片段将字节 0x4A、0x43 和 0x4B 放入代码中：  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  如果 `_emit` 生成了修改寄存器的指令，并且您在编译应用程序时进行了优化，则编译器无法确定受到影响的寄存器。 例如，如果`_emit`生成一个指令，修改**rax**寄存器，编译器将不知道**rax**已更改。 在内联汇编程序代码执行后，编译器随后可能会对该寄存器中的值做出错误假设。 因此，在应用程序运行时，它可能展示出不可预知的行为。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)