---
title: 编译器错误 C3071 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3071
dev_langs:
- C++
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 163cb170953c444789e39b906ff4d408739f7514
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3071"></a>编译器错误 C3071
运算符“operator”只能应用于 ref 类或值类型实例中  
  
 不能在本机类型上使用 CLR 运算符。 可以在 ref 类或 ref 结构（值类型）上使用运算符，但不可在本机类型（如 int）或本机类型的别名（如 System::Int32）上使用。 这些类型不能从 C++ 代码中以引用本机变量的方式进行装箱，因此无法使用此运算符。  
  
 有关详细信息，请参阅[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C3071。  
  
```  
// C3071.cpp  
// compile with: /clr  
class N {};  
ref struct R {};  
  
int main() {  
   N n;  
   %n;   // C3071  
  
   R r;  
   R ^ r2 = %r;   // OK  
}  
```