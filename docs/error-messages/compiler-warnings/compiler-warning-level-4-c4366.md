---
title: "编译器警告 （等级 4） C4366 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 221cc02e5a2592599bad0ee9a77de59b19dda6f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4366"></a>编译器警告（等级 4）C4366
一元 operator 运算符的结果可能是未对齐  
  
 如果由于装箱，结构成员曾经可能是未对齐，编译器将发出警告时该成员的地址将分配给非对齐的指针。 默认情况下，所有指针都被都对齐。  
  
 若要解决 C4366，请更改结构的对齐方式，或声明指针[__unaligned](../../cpp/unaligned.md)关键字。  
  
 有关详细信息，请参阅 __unaligned 和[包](../../preprocessor/pack.md)。  
  
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