---
title: 编译器错误 C3374 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3374
dev_langs:
- C++
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd06f0e63ab1c467b9359c38ad77056440535aba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253887"
---
# <a name="compiler-error-c3374"></a>编译器错误 C3374
不能采用“函数”的地址，除非创建委托实例  
  
 在上下文中而不是委托实例的创建中采用函数的地址。  
  
 以下示例生成 C3374：  
  
```  
// C3374.cpp  
// compile with: /clr  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      System::Console::WriteLine("in func1 {0}", i);  
   }  
};  
  
int main() {  
   &A::func1;   // C3374  
  
   // OK  
   A ^ a = gcnew A;  
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [如何：定义和使用委托 (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)