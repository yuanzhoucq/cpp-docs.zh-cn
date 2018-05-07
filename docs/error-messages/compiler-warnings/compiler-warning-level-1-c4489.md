---
title: 编译器警告 （等级 1） C4489 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4489
dev_langs:
- C++
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1c6cff47d8788edd7fdba6844e07d59654456a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4489"></a>编译器警告（等级 1）C4489
specifier： 不允许对接口方法 method;重写说明符仅可以在 ref 类和值类方法  
  
 在接口方法上不正确地使用说明符关键字。  
  
 有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4489。  
  
```  
// C4489.cpp  
// compile with: /clr /c /W1  
public interface class I {   
   void f() new;   // C4489  
   virtual void b() override;   // C4489  
  
   void g();   // OK  
};  
```