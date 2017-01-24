---
title: "bss_seg | Microsoft Docs"
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
  - "vc-pragma.bss_seg"
  - "bss_seg_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "bss_seg 杂注"
  - "杂注, bss_seg"
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bss_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定其中的未初始化变量存储在 .obj 文件中的段。  
  
## 语法  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 备注  
 可使用 [dumpbin](../build/reference/dumpbin-command-line.md) 应用程序查看 Obj 文件。  未初始化数据的 .obj 文件中的默认段为 .bss。  在某些情况下，使用 **bss\_seg** 可将未初始化的数据分组到一个节，从而缩短加载时间。  
  
 没有参数的 **bss\_seg** 会将此段重置为 .bss。  
  
 **push**（可选）  
 将一个记录置于内部编译器堆栈上。  **push** 可具有 *identifier* 和 *segment\-name*。  
  
 **pop**（可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 *identifier*（可选）  
 当与 **push** 一起使用时，为内部编译器堆栈上的记录指定名称。  当与 **pop** 一起使用时，将从内部堆栈中弹出记录，直到删除 *identifier*；如果未在内部堆栈中找到 *identifier*，则不会弹出任何内容。  
  
 利用 *identifier*，可使多个记录与一个 **pop** 命令一起弹出。  
  
 *"segment\-name"*（可选）  
 段的名称。当与 **pop** 一起使用时，将弹出堆栈并且 *segment\-name* 将变为活动的段名称。  
  
 *"segment\-class"* （可选）  
 包括与 2.0 版之前的 C\+\+ 的兼容性。  它将被忽略。  
  
## 示例  
  
```  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 您还可为已初始化的数据 \([data\_seg](../preprocessor/data-seg.md)\)、函数 \([code\_seg](../preprocessor/code-seg.md)\) 和常量变量 \([const\_seg](../preprocessor/const-seg.md)\) 指定节。  
  
 使用 **bss\_seg** 杂注分配的数据不会保留有关其位置的任何信息。  
  
 有关在创建部分时不应使用的名称的列表，请参阅 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)