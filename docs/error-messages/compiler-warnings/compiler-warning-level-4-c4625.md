---
title: 编译器警告 （等级 4） C4625 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4625
dev_langs:
- C++
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9279d5a9bfa7aa80ae866d290624f1edf888e36b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297428"
---
# <a name="compiler-warning-level-4-c4625"></a>编译器警告（等级 4）C4625
“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问或已被删除  
  
 复制构造函数已删除或在基类中不可访问，因此并未为派生类生成。 复制此类型的对象的任何尝试都将导致编译器错误。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4625，并演示如何修复此错误。  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```