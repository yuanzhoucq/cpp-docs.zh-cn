---
title: 编译器错误 C3612 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e07c899dbacdc58e9048ffa21d6be1b6abc02632
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252840"
---
# <a name="compiler-error-c3612"></a>编译器错误 C3612
type： 密封的类不能是抽象  
  
使用定义的类型`value`默认情况下，都密封的而类是抽象的除非它实现其基类的所有方法。 密封的抽象类可以既不是基类，也可以将它实例化。  
  
有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
下面的示例生成 C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```