---
title: 编译器警告（等级 4）C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 11fcb0070359201de39ca5f33c83d000e02f0835
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391551"
---
# <a name="compiler-warning-level-4-c4366"></a>编译器警告（等级 4）C4366

一元 operator 运算符的结果可能是未对齐

如果由于装箱，结构成员以往可能是未对齐，编译器会警告时成员的地址分配到非对齐的指针。 默认情况下，对齐的所有指针。

若要解决 C4366，请更改结构的对齐方式或使用指针声明[__unaligned](../../cpp/unaligned.md)关键字。

有关详细信息，请参阅 __unaligned 并[pack](../../preprocessor/pack.md)。

## <a name="example"></a>示例

下面的示例生成 C4366。

```
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