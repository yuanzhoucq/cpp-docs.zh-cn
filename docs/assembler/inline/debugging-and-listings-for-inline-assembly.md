---
title: "调试和列出内联程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 调试"
  - "Bug, __asm 块"
  - "调试 [C++], 内联程序集代码"
  - "内联程序集, 调试"
  - "内联程序集, 列表"
  - "源级别调试器"
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 调试和列出内联程序集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 如果您使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 选项进行编译，则可使用源级别调试器调试包含内联程序集代码的程序。  
  
 在调试器中，您可在 C 或 C\+\+ 和汇编语言行上设置断点。  如果启用混合程序集和源模式，则可同时显示程序集代码的源形式和反汇编形式。  
  
 请注意，在一行上放置多个程序集指令或源语言语句可能妨碍调试。  在源模式中，您可使用调试器在单行上设置断点，但不是在同一行的各个语句上。  相同的准则适用于定义为一个 C 宏（用于扩展到单个逻辑行）的 `__asm` 块。  
  
 如果使用 [\/FAs](../../build/reference/fa-fa-listing-file.md) 编译器选项创建混合源和汇编列表，则列表将包含每个汇编语言行的源形式和汇编形式。  宏在列表中将不会扩展，但会在编译时扩展。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)