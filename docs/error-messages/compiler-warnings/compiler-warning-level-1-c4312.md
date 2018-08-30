---
title: 编译器警告 （等级 1） C4312 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4312
dev_langs:
- C++
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b30d020532935c925b1ecab25d17cd43a7e8663
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205897"
---
# <a name="compiler-warning-level-1-c4312"></a>编译器警告（等级 1）C4312
“operation”: 从“type1”转换到更大的“type2”  
  
 此警告检测将 32 位值分配给 64 位指针类型的尝试，例如，将 32 位 `int` 或 `long` 强制转换为 64 位指针。  
  
 这可能是不安全的转换，即使对于在发生符号扩展时适应 32 位的指针值也是如此。 如果为 64 位指针类型分配负 32 位整数，则符号扩展会导致指针值引用的内存地址与整数的值不同。  
  
 仅对 64 位编译目标发出此警告。 有关详细信息，请参阅[使用指针的规则](/windows/desktop/WinProg64/rules-for-using-pointers)。  
  
 以下代码示例在其针对 64 位目标进行编译时将生成 C4312：  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```