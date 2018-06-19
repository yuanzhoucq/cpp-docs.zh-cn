---
title: 编译器错误 C3766 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3766
dev_langs:
- C++
helpviewer_keywords:
- C3766
ms.assetid: b5af2089-2e1e-4e45-a41d-495b6c55656e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1467f36757495734018c1ebac9c0a8b115d2919
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267066"
---
# <a name="compiler-error-c3766"></a>编译器错误 C3766
type 必须提供接口的实现方法 function  
  
 从接口继承的类必须实现接口成员。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3766。  
  
```  
// C3766.cpp  
// compile with: /clr /c  
  
delegate void MyDel();  
  
interface struct IFace {  
   virtual event MyDel ^ E;  
};  
  
ref struct Class1 : public IFace {};   // C3766  
  
// OK  
ref struct Class2 : public IFace {  
   virtual event MyDel ^ E {  
      void add(MyDel ^) {}  
      void remove(MyDel ^) {}  
   }  
};  
```