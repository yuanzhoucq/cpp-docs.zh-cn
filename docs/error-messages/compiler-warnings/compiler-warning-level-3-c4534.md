---
title: "编译器警告 （等级 3） C4534 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: c4534
dev_langs: C++
helpviewer_keywords: C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d9ea2cc6fb15edf61610e96a728e985b78be468
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4534"></a>编译器警告（等级 3）C4534
constructor 将不会类 class 由于默认自变量的默认构造函数  
  
 非托管的类可以具有具有默认值的参数的构造函数并编译器将使用此默认构造函数。 类用来标记`value`关键字将不使用构造函数使用默认值为其参数作为默认构造函数。  
  
 有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下面的示例生成 C4534:  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```