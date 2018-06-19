---
title: 编译器警告 （等级 1） C4488 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3c5fc64637d989066acfa90715c50504664231
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281517"
---
# <a name="compiler-warning-level-1-c4488"></a>编译器警告（等级 1）C4488
function： 需要 keyword 关键字实现接口方法 interface_method  
  
 类必须实现它从直接基类继承的接口的所有成员。 实现的成员必须具有公共可访问性，并且必须标记为虚拟。  
  
## <a name="example"></a>示例  
 如果实现的成员不是公共则可能发生 C4488。 下面的示例生成 C4488。  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## <a name="example"></a>示例  
 如果实现的成员未标记为虚拟，可能发生 C4488。 下面的示例生成 C4488。  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```