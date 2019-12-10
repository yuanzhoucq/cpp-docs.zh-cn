---
title: 编译器警告（等级 4）C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: fb4cead9367c5ef69627f607c521f480ad94271f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991051"
---
# <a name="compiler-warning-level-4-c4366"></a>编译器警告（等级 4）C4366

一元运算符 "operator" 运算符的结果可能是未对齐的

如果结构成员由于打包而无法进行不对齐，则在将该成员的地址分配给对齐指针时，编译器将发出警告。 默认情况下，所有指针都对齐。

若要解析 C4366，请更改结构的对齐方式，或用[__unaligned](../../cpp/unaligned.md)关键字声明指针。

有关详细信息，请参阅 __unaligned 和[pack](../../preprocessor/pack.md)。

## <a name="example"></a>示例

下面的示例生成 C4366。

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```
