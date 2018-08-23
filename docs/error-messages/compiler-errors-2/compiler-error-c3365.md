---
title: 编译器错误 C3365 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3365
dev_langs:
- C++
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a41fc5b1eb5c93bf73685b5141bd91ab7a6058e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252515"
---
# <a name="compiler-error-c3365"></a>编译器错误 C3365
运算符“operator”: 区分类型为“type1”和“type2”的操作数  
  
已尝试撰写具有不同类型的委托。  请参阅[如何： 定义和使用委托 (C + + /cli CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)有关委托的详细信息。  
  
## <a name="example"></a>示例  
以下示例生成 C3365：  
  
```cpp  
// C3365.cpp  
// compile with: /clr  
delegate void D1();  
delegate void D2(int);  
  
ref class R {  
public:  
   void f(){}  
   void g(int){}  
};  
  
int main() {  
   D1^ d1 = gcnew D1(gcnew R, &R::f);  
   D2^ d2 = gcnew D2(gcnew R, &R::g);  
   D1^ d3 = gcnew D1(gcnew R, &R::f);  
  
   d1 += d2;   // C3365  
   d1 += d3;   // OK  
   d1();  
}  
```