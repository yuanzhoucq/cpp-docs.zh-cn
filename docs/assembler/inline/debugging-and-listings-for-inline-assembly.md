---
title: "内联程序集的调试和列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fea943c30d48ac122ae5d848306e4fe251f58da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-listings-for-inline-assembly"></a>内联程序集的调试和列表
## <a name="microsoft-specific"></a>Microsoft 专用  
 如果使用进行编译，可以使用源级别调试器调试包含内联程序集代码的程序[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项。  
  
 在调试器中，您可在 C 或 C++ 和汇编语言行上设置断点。 如果启用混合程序集和源模式，则可同时显示程序集代码的源形式和反汇编形式。  
  
 请注意，在一行上放置多个程序集指令或源语言语句可能妨碍调试。 在源模式中，您可使用调试器在单行上设置断点，但不是在同一行的各个语句上。 相同的准则适用于定义为一个 C 宏（用于扩展到单个逻辑行）的 `__asm` 块。  
  
 如果创建混合的源和汇编列表与[/FAs](../../build/reference/fa-fa-listing-file.md)编译器选项，该列表包含的每个汇编语言行的源和程序集窗体。 宏在列表中将不会扩展，但会在编译时扩展。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)