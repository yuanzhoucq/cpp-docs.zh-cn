---
title: 编译器警告 （等级 1） C4407 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9a665dbb71157b37f72d3d0721357d00dc37230
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032596"
---
# <a name="compiler-warning-level-1-c4407"></a>编译器警告（等级 1）C4407

指向成员表示形式的不同指针之间强制转换，编译器可能生成不正确的代码

检测到不正确的转换。

由于 Visual c + + 2005年中执行的编译器一致性工作，可以生成 C4407。 指向成员的指针现在需要限定名称和 address-of 运算符 (&)。

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