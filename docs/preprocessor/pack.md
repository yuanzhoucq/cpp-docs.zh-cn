---
title: 包 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs:
- C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c29c31cae2b7de59d4db5ed6546ad4eda6baecf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843621"
---
# <a name="pack"></a>pack
指定结构、联合和类成员的封装对齐。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>备注  
 封装类是在内存中将其一个成员直接放在另一个后面，这可能表示对齐部分或全部成员的边界可以小于默认对齐目标体系结构。 `pack` 提供了数据声明级别的控制。 这不同于编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md)，这只提供模块级别控制。 在杂注出现之后，`pack` 在第一个 `struct`、`union` 或 `class` 声明处生效。 `pack` 对定义没有影响。 调用`pack`使用没有自变量集`n`编译器选项中设置的值为 **/Zp**。 如果未设置编译器选项，则默认值为 8。  
  
 如果更改某个结构的对齐方式，它可能不会使用像内存中一样多的空间，但您可能会发现性能降低或者甚至是因未对齐访问而遇到硬件产生的异常。  你可以通过使用修改此异常行为[SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621)。  
  
 **显示**（可选）  
 显示封装对齐的当前字节值。 该值由警告消息显示。  
  
 **推送**（可选）  
 将当前封装对齐值推送到内部编译器堆栈上，并将当前封装对齐值设置为 `n`。 如果未指定 `n`，则将推送当前封装对齐值。  
  
 **pop** （可选）  
 从内部编译器堆栈的顶部移除记录。 如果`n`未使用指定**pop**，则与堆栈顶部的生成的记录关联的封装值是新封装对齐值。 如果指定了 `n`（例如 `#pragma pack(pop, 16)`），`n` 将成为新的封装对齐值。 如果使用 `identifier`（例如 `#pragma pack(pop, r1)`）进行弹出，则堆栈上的所有记录都将弹出，直到找到包含 `identifier` 的记录。 该记录将会弹出，与堆栈顶部的生成的记录关联的封装值是新的封装对齐值。 如果使用`identifier`在堆栈上的任何记录中未找到则**pop**将被忽略。  
  
 `identifier`（可选）  
 如果用于**推送**，将名称分配给内部编译器堆栈上的记录。 如果用于**pop**，从之前的内部堆栈中弹出记录`identifier`被删除; 如果`identifier`找不到在内部堆栈上，会弹出任何内容。  
  
 `n`（可选）  
 指定要用于封装的值（以字节为单位）。 如果编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md)模块的默认值未设置`n`为 8。 有效值为 1、2、4、8 和 16。 成员将在作为 `n` 的倍数或成员的大小的倍数的边界（以较小者为准）上对齐。  
  
 `#pragma pack(pop, identifier, n)` 未定义。  
  
 有关如何修改对齐方式的详细信息，请参阅以下主题：  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [结构对齐示例](../build/examples-of-structure-alignment.md)(特定于 x64)  
  
    > [!WARNING]
    >  请注意，在 Visual Studio 2015 和更高版本可使用标准的 alignas 和 alignof 运算符，这 不同于 `__alignof` 和 `declspec( align )`，它们是跨编译器可移植的。 C++ 标准不能解决封装，因此仍必须使用 `pack`（或其他编译器上相应的扩展）来指定小于目标体系结构字体大小的对齐方式。  
  
## <a name="example"></a>示例  
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
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**推送**， **pop**，和**显示**语法。  
  
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
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)