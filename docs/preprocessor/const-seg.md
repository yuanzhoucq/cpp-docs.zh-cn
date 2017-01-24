---
title: "const_seg | Microsoft Docs"
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
  - "vc-pragma.const_seg"
  - "const_seg_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "const_seg 杂注"
  - "杂注, const_seg"
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# const_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 .obj 文件中存储 [const](../cpp/const-cpp.md) 变量的段。  
  
## 语法  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 备注  
 本主题中的术语“段”和“节”的含义是可互换的。  
  
 可使用 [dumpbin](../build/reference/dumpbin-command-line.md) 应用程序查看 OBJ 文件。  .obj 文件中针对 `const` 变量的默认段是 .rdata。  某些 `const` 变量（如标量）将自动内联到代码流中。  内联代码将不会显示在 .rdata 中。  
  
 在 `const_seg` 中定义需要动态初始化的对象会导致未定义的行为。  
  
 不带参数的 `#pragma const_seg` 会将段重置为 .rdata。  
  
 `push`（可选）  
 将一个记录置于内部编译器堆栈上。  `push` 可以有一个 `identifier` 和 `segment-name`。  
  
 `pop`（可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 `identifier`（可选）  
 当与 `push` 一起使用时，为内部编译器堆栈上的记录指定名称。  当与 `pop` 一起使用时，从内部堆栈中弹出记录，直到移除 `identifier`；如果未在内部堆栈上找到 `identifier`，则不会弹出任何内容。  
  
 使用 `identifier` 可实现只用一个 `pop` 命令弹出多个记录。  
  
 “`segment-name`”（可选）  
 段的名称。  堆栈与 `pop` 配合使用时将弹出，并且 `segment-name` 会成为活动段名称。  
  
 “`segment-class`”（可选）  
 包括与 2.0 版之前的 C\+\+ 的兼容性。  它将被忽略。  
  
## 示例  
  
```  
// pragma_directive_const_seg.cpp  
// compile with: /EHsc  
#include <iostream>  
  
const int i = 7;               // inlined, not stored in .rdata  
const char sz1[]= "test1";     // stored in .rdata  
  
#pragma const_seg(".my_data1")  
const char sz2[]= "test2";     // stored in .my_data1  
  
#pragma const_seg(push, stack1, ".my_data2")  
const char sz3[]= "test3";     // stored in .my_data2  
  
#pragma const_seg(pop, stack1) // pop stack1 from stack  
const char sz4[]= "test4";     // stored in .my_data1  
  
int main() {  
    using namespace std;  
   // const data must be referenced to be put in .obj  
   cout << sz1 << endl;  
   cout << sz2 << endl;  
   cout << sz3 << endl;  
   cout << sz4 << endl;  
}  
```  
  
  **test1**  
**test2**  
**test3**  
**test4**   
## 批注  
 有关在创建部分时不应使用的名称的列表，请参阅 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 你还可以为初始化的数据 \([data\_seg](../preprocessor/data-seg.md)\)、未初始化的数据 \([bss\_seg](../preprocessor/bss-seg.md)\) 和函数 \([code\_seg](../preprocessor/code-seg.md)\) 指定部分。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)