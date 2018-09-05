---
title: 内联程序集的调试和列表 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6cca954ae15252b97d883ba8491fdb98e506f68
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689284"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>内联程序集的调试和列表

**Microsoft 专用**

可以使用源级别调试器调试包含内联程序集代码的程序，如果使用编译[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项。

在调试器中，您可在 C 或 C++ 和汇编语言行上设置断点。 如果启用混合程序集和源模式，则可同时显示程序集代码的源形式和反汇编形式。

请注意，在一行上放置多个程序集指令或源语言语句可能妨碍调试。 在源模式中，您可使用调试器在单行上设置断点，但不是在同一行的各个语句上。 相同的准则适用于定义为一个 C 宏（用于扩展到单个逻辑行）的 `__asm` 块。

如果创建混合的源和程序集列表与[/FAs](../../build/reference/fa-fa-listing-file.md)编译器选项时，该列表包含的每个汇编语言行的源和程序集窗体。 宏在列表中将不会扩展，但会在编译时扩展。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>