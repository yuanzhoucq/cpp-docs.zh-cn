---
title: 编译器错误 C3375 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3375
dev_langs:
- C++
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11805b7ef714c65ff9816828aeea10baa2217ff6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3375"></a>编译器错误 C3375
“function”：不明确的委托函数  
  
 委托实例化可能已为静态成员函数，或为实例函数未绑定的委托，因此编译器出现此错误。  
  
 有关详细信息，请参阅[委托 （c + + 组件扩展）](../../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C3375：  
  
```  
// C3375.cpp  
// compile with: /clr  
ref struct R {  
   static void f(R^) {}  
   void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::f);   // C3375  
}  
```