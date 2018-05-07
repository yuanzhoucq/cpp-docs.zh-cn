---
title: 编译器警告 （等级 1） C4407 |Microsoft 文档
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
ms.openlocfilehash: cbc02c32463703f658cef1d5756926311d89b193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4407"></a>编译器警告（等级 1）C4407
指向成员表示形式不同的指针之间强制转换，编译器也会生成不正确的代码  
  
 检测到不正确的转换。  
  
 由于在 Visual c + + 2005年中完成的编译器一致性工作可以生成 C4407。 指向成员的指针现在需要限定名称和 address-of 运算符 (&)。  
  
 如果你多个继承指针到成员到单一继承指针到成员之间强制转换，则会发生 C4407。 有时这种做法，但有时它无法，因为单一继承指向成员的指针表示拥有足够的信息。 使用编译 **/vmm**可能帮助 (有关详细信息，请参阅[/vmm、 /vms、 /vmv （通用表示形式）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md))。 你还可以尝试重新排列你基类;编译器检测信息丢失在转换过程中由于基类是从派生非零偏移量的位置。  
  
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