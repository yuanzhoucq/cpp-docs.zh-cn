---
title: "code_seg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "code_seg_CPP"
  - "vc-pragma.code_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "code_seg 杂注"
  - "杂注, code_seg"
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# code_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 .obj 文件中存储函数的文本段。  
  
## 语法  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 备注  
 `code_seg` 杂注指令不控制为实例化模板生成的对象代码和编译器隐式生成的代码（例如特殊成员函数）的放置位置。  我们建议你使用 [\_\_declspec\(code\_seg\(...\)\)](../cpp/code-seg-declspec.md) 特性，因为使用它可控制所有对象代码的放置位置。  其中包括编译器生成的代码。  
  
 .obj 文件中的段是作为一个单元加载到内存的已命名数据块。  “文本段”是包含可执行代码的段。  在本文中，术语“段”和“节”可互换使用。  
  
 `code_seg` 杂注指令指示编译器将翻译单元中的所有后续对象代码放入到名为 `segment-name` 的文本段中。  默认情况下，.obj 文件中用于函数的文本段的名称为 .text。  
  
 无参数的 `code_seg` 杂注指令将后续对象代码的文本段名称重置为 .text。  
  
 **Push**（可选）  
 将一个记录置于内部编译器堆栈上。  **push** 可以有一个 `identifier` 和 `segment-name`。  
  
 **pop**（可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 `identifier`（可选）  
 当与 **push** 一起使用时，为内部编译器堆栈上的记录指定名称。  当与 **pop** 一起使用时，从内部堆栈中弹出记录，直到移除 `identifier`；如果未在内部堆栈上找到 `identifier`，则不会弹出任何内容。  
  
 `identifier` 可实现只用一个 **pop** 命令弹出多个记录。  
  
 “`segment-name`”（可选）  
 段的名称。  堆栈与 **pop** 配合使用时将弹出，并且 `segment-name` 会成为活动文本段名称。  
  
 “`segment-class`”（可选）  
 忽略但被包含，以便与 2.0 版之前的 C\+\+ 版本兼容。  
  
 你可以使用 [DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) 应用程序查看 .obj 文件。  用于每个支持的目标体系结构的 DUMPBIN 版本随 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 一起提供。  
  
## 示例  
 以下示例演示如何使用 `code_seg` 杂注指令控制对象代码的放置位置：  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 有关不应用于创建节的名称的列表，请参阅 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 你还可以为初始化的数据 \([data\_seg](../preprocessor/data-seg.md)\)、未初始化的数据 \([bss\_seg](../preprocessor/bss-seg.md)\) 和常量变量 \([const\_seg](../preprocessor/const-seg.md)\) 指定部分。  
  
## 请参阅  
 [code\_seg \(\_\_declspec\)](../cpp/code-seg-declspec.md)   
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)