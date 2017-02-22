---
title: "pack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pack_CPP"
  - "vc-pragma.pack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "包装杂注"
  - "杂注, 包装"
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# pack
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定结构、联合和类成员的封装对齐。  
  
## 语法  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## 备注  
 封装类是在内存中将其一个成员直接放在另一个后面，这可能表示对齐部分或全部成员的边界可以小于默认对齐目标体系结构。  `pack` 提供了数据声明级别的控制。  这与编译器选项 [\/Zp](../build/reference/zp-struct-member-alignment.md) 不同，该选项只提供模块级别控制。  在杂注出现之后，`pack` 在第一个 `struct`、`union` 或 `class` 声明处生效。  `pack` 对定义没有影响。  在没有参数的情况下调用 `pack` 会将 `n` 设置为编译器选项 **\/Zp** 中设置的值。  如果未设置编译器选项，则默认值为 8。  
  
 如果更改某个结构的对齐方式，它可能不会使用像内存中一样多的空间，但您可能会发现性能降低或者甚至是因未对齐访问而遇到硬件产生的异常。  您可以使用 [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621) 修改此异常行为。  
  
 **show** （可选）  
 显示封装对齐的当前字节值。  该值由警告消息显示。  
  
 **push** （可选）  
 将当前封装对齐值推送到内部编译器堆栈上，并将当前封装对齐值设置为 `n`。  如果未指定 `n`，则将推送当前封装对齐值。  
  
 **pop** （可选）  
 从内部编译器堆栈的顶部移除记录。  如果没有用 `n` 指定 **pop**，则与堆栈顶部的生成的记录关联的封装值是新的封装对齐值。  如果指定了 `n`（例如 `#pragma pack(pop, 16)`），`n` 将成为新的封装对齐值。  如果使用 `identifier`（例如 `#pragma pack(pop, r1)`）进行弹出，则堆栈上的所有记录都将弹出，直到找到包含 `identifier` 的记录。  该记录将会弹出，与堆栈顶部的生成的记录关联的封装值是新的封装对齐值。  如果使用在堆栈上的任何记录中均未发现的 `identifier` 进行弹出，则会忽略 **pop**。  
  
 `identifier` （可选）  
 当与 **push** 一起使用时，为内部编译器堆栈上的记录指定名称。  当与 **pop** 一起使用时，从内部堆栈中弹出记录，直到移除 `identifier`；如果未在内部堆栈上找到 `identifier`，则不会弹出任何内容。  
  
 `n`（可选）  
 指定要用于封装的值（以字节为单位）。  如果没有为模块设置编译器选项 [\/Zp](../build/reference/zp-struct-member-alignment.md)，`n` 的默认值为 8。  有效值为 1、2、4、8 和 16。  成员将在作为 `n` 的倍数或成员的大小的倍数的边界（以较小者为准）上对齐。  
  
 `#pragma pack(pop,` `identifier``,` `n``)` 是不确定的。  
  
 有关如何修改对齐方式的详细信息，请参阅以下主题：  
  
-   [\_\_alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_unaligned](../cpp/unaligned.md)  
  
-   [结构对齐示例](../build/examples-of-structure-alignment.md)（特定于 x64）  
  
    > [!WARNING]
    >  请注意，在 Visual Studio 2015 和更高版本可使用标准的 alignas 和 alignof 运算符，这 不同于 `__alignof` 和 `declspec( align )`，它们是跨编译器可移植的。  C\+\+ 标准不能解决封装，因此仍必须使用 `pack`（或其他编译器上相应的扩展）来指定小于目标体系结构字体大小的对齐方式。  
  
## 示例  
 以下示例演示如何使用 `pack` 杂注更改结构的对齐方式。  
  
```  
// pragma_directives_pack.cpp  
#include <stddef.h>  
#include <stdio.h>  
  
struct S {  
   int i;   // size 4  
   short j;   // size 2  
   double k;   // size 8  
};  
  
#pragma pack(2)  
struct T {  
   int i;  
   short j;  
   double k;  
};  
  
int main() {  
   printf("%zu ", offsetof(S, i));  
   printf("%zu ", offsetof(S, j));  
   printf("%zu\n", offsetof(S, k));  
  
   printf("%zu ", offsetof(T, i));  
   printf("%zu ", offsetof(T, j));  
   printf("%zu\n", offsetof(T, k));  
}  
```  
  
```  
0 4 8  
0 4 6  
```  
  
## 示例  
 以下示例演示如何使用 **push**、**pop** 和 **show** 语法。  
  
```  
// pragma_directives_pack_2.cpp  
// compile with: /W1 /c  
#pragma pack()   // n defaults to 8; equivalent to /Zp8  
#pragma pack(show)   // C4810  
#pragma pack(4)   // n = 4  
#pragma pack(show)   // C4810  
#pragma pack(push, r1, 16)   // n = 16, pushed to stack  
#pragma pack(show)   // C4810  
#pragma pack(pop, r1, 2)   // n = 2 , stack popped  
#pragma pack(show)   // C4810  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)