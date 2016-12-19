---
title: "data_seg | Microsoft Docs"
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
  - "data_seg_CPP"
  - "vc-pragma.data_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "data_seg 杂注"
  - "杂注, data_seg"
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# data_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 .obj 文件中用于存储初始化变量的数据段。  
  
## 语法  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 备注  
 本主题中的术语“段”和“节”的含义是可互换的。  
  
 可使用 [dumpbin](../build/reference/dumpbin-command-line.md) 应用程序查看 OBJ 文件。  .obj 文件中用于存储初始化变量的默认段是 .data。  未初始化的变量被视为初始化为零并且存储在 .bss 中。  
  
 不带参数的 **data\_seg** 将段重置为 .data。  
  
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
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 使用 **data\_seg** 分配的数据不保留有关其位置的任何信息。  
  
 有关在创建部分时不应使用的名称的列表，请参阅 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 您还可以为常量变量 \([const\_seg](../preprocessor/const-seg.md)\)、未初始化的数据 \([bss\_seg](../preprocessor/bss-seg.md)\) 和函数 \([code\_seg](../preprocessor/code-seg.md)\) 指定部分。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)