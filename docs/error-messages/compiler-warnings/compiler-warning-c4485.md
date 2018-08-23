---
title: 编译器警告 C4485 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b84d2976e31d5cc3a9b6547d0c4b02a61327ce0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270433"
---
# <a name="compiler-warning-c4485"></a>编译器警告 C4485
override_function: ref 基类类方法 base_class_function 相匹配，但不是标记 new 或重写';假定 new （和虚拟）  
  
 访问器中重写时，带有或不带`virtual`关键字、 基类访问器函数，但`override`或`new`说明符不是重写的函数签名的一部分。 添加`new`或`override`说明符若要解决此警告。  
  
 请参阅[重写](../../windows/override-cpp-component-extensions.md)和[新 (新 vtable 中的槽）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)有关详细信息。  
  
 C4485 始终作为错误发出。 使用[警告](../../preprocessor/warning.md)杂注可取消 C4485。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```