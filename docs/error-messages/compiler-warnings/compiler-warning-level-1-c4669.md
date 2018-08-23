---
title: 编译器警告 （等级 1） C4669 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4669
dev_langs:
- C++
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baffb413a5c07acaeea7f4706ab9d6e951c65f04
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280177"
---
# <a name="compiler-warning-level-1-c4669"></a>编译器警告（等级 1）C4669
“cast”: 不安全的转换:“class”是托管的或 WinRT 类型对象  
  
 转换包含 Windows 运行时或托管类型。 编译器通过执行到一个指针到另一个指针的按位复制完成转换，但不提供其他检查。 若要解决此警告，请不要转换包含托管成员或 Windows 运行时类型的类。  
  
 下面的示例生成 C4669，并演示如何修复此错误：  
  
```  
// C4669.cpp  
// compile with: /clr /W1  
ref struct A {  
   int i;  
   Object ^ pObj;   // remove the managed member to fix the warning  
};  
  
ref struct B {  
   int j;  
};  
  
int main() {  
   A ^ a = gcnew A;  
   B ^ b = reinterpret_cast<B ^>(a);   // C4669  
}  
```