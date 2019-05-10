---
title: 编译器警告（等级 1）C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 2e47e293b650f64d2a6be91a837cc4195e073e8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447742"
---
# <a name="compiler-warning-level-1-c4407"></a>编译器警告（等级 1）C4407

指向成员表示形式的不同指针之间强制转换，编译器可能生成不正确的代码

检测到不正确的转换。

由于 Visual Studio 2005 中执行的编译器一致性工作，可以生成 C4407。 指向成员的指针现在需要限定的名称和 address-of 运算符 (&)。

如果多个继承成员的指针到-到单一继承成员的指针到-之间强制转换，则会发生 C4407。 有时可以这样做，但有时不能因为单一继承成员的指针表示形式不会保留足够的信息。 使用编译 **/vmm**可能有助于 (有关详细信息，请参阅[/vmm、 /vms、 /vmv （通用表示形式）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md))。 此外可以尝试重新排列基类;编译器在转换过程中检测信息丢失，因为基类为非零偏移量位置处的派生。

下面的示例生成 C4407:

```
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```