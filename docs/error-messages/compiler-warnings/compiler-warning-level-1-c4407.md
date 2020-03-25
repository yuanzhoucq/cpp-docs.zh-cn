---
title: 编译器警告（等级 1）C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 8dd78872d4edf82fb61c8ab93639dbcd93085754
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162538"
---
# <a name="compiler-warning-level-1-c4407"></a>编译器警告（等级 1）C4407

在不同指针到成员表示形式之间强制转换，编译器可能生成不正确的代码

检测到不正确的强制转换。

由于在 Visual Studio 2005 中执行了编译器一致性工作，因此可能生成 C4407。 指向成员的指针现在需要限定名和地址（&）。

如果在多个继承指向成员的指针之间进行强制转换，则可能会发生 C4407。 有时这可以正常工作，但有时不能这样做，因为单个继承指针到成员的表示形式不包含足够的信息。 用 **/vmm**进行编译可能会有所帮助（有关详细信息，请参阅[/vmm、/vms、/Vmv （常规用途表示形式）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)。 你还可以尝试重新排列基类;编译器检测到转换中的信息丢失，因为基类与派生的非零偏移量。

下面的示例生成 C4407：

```cpp
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
