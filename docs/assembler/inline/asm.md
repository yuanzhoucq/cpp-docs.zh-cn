---
title: "__asm | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__asm"
  - "__asm_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++]"
  - "__asm 关键字 [C++], 与 asm 块"
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __asm
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `__asm` 关键字用于调用内联汇编程序，并且可在 C 或 C\+\+ 语句合法时出现。  它不能单独出现。  它必须后跟一个程序集指令、一组括在大括号中的指令或者至少一对空大括号。  此处的术语“`__asm` 块”指任何指令或指令组（无论是否在大括号中）。  
  
> [!NOTE]
>  Visual C\+\+ 对标准 C\+\+ `asm` 关键字的支持仅限于编译器不会生成与此关键字有关的错误这一事实。  但是，`asm` 块不会生成任何有意义的代码。  使用 `__asm` 而非 `asm`。  
  
 语法：  
  
 \_\_asm *assembly\-instruction* \[ ; \]  
  
 \_\_asm { *assembly\-instruction\-list* } \[ ; \]  
  
## 语法  
 `__asm`  `assembly-instruction`  `;` opt  
  
 `__asm {`  `assembly-instruction-list`  `};` opt  
  
 *assembly\-instruction\-list*:  
 `assembly-instruction` `;` opt  
  
 `assembly-instruction` `;` `assembly-instruction-list` `;` opt  
  
 如果不与大括号一起使用，则 `__asm` 关键字表示此行的其余部分是一条汇编语言语句。  如果与大括号一起使用，则该关键字表示大括号之间的每一行都是一条汇编语言语句。  为了与早期版本兼容，`_asm` 是 `__asm` 的同义词。  
  
 由于 `__asm` 关键字是语句分隔符，因此您可以将程序集指令放在同一行中。  
  
 在 Visual C\+\+ 2005 之前，指令  
  
```  
__asm int 3  
```  
  
 不会导致在使用 **\/clr** 编译时生成本机代码；编译器会将该指令转换为 CLR 中断指令。  
  
 `__asm int 3` 现在将导致为函数生成本机代码。  如果您希望函数导致代码中出现断点，还希望将函数编译为 MSIL，请使用 [\_\_debugbreak](../../intrinsics/debugbreak.md)。  
  
## 示例  
 以下代码片段是括在大括号里的简单 `__asm` 块：  
  
```  
__asm {  
   mov al, 2  
   mov dx, 0xD007  
   out dx, al  
}  
```  
  
 或者，您还可以将 `__asm` 放在每个程序集指令前面：  
  
```  
__asm mov al, 2  
__asm mov dx, 0xD007  
__asm out dx, al  
```  
  
 由于 `__asm` 关键字是语句分隔符，因此您还可将程序集指令放在同一行中：  
  
```  
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al  
```  
  
 这三个示例将生成相同的代码，但第一个样式（用大括号括起 `__asm` 块）具有一些优势。  大括号可清楚地将程序集代码与 C 或 C\+\+ 代码分隔开，并避免了不必要的 `__asm` 关键字重复。  大括号还可防止二义性。  如果要将 C 或 C\+\+ 语句放在与 `__asm` 块相同的行上，则必须将此块括在大括号中。  如果没有大括号，编译器将无法告知程序集代码的停止位置以及 C 或 C\+\+ 语句的开始位置。  最后，由于大括号中的文本与普通 MASM 文本具有相同的格式，因此您可以轻松从现有 MASM 源文件剪切并粘贴文本。  
  
 不同于 C 和 C\+\+ 中的大括号，括起 `__asm` 块的大括号不会影响变量范围。  您也可以嵌套 `__asm` 块；嵌套不影响变量范围。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C\+\+ 关键字](../../cpp/keywords-cpp.md)   
 [内联汇编程序](../../assembler/inline/inline-assembler.md)