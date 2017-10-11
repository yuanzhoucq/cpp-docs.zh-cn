---
title: "编译器错误 C3768 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3768
dev_langs:
- C++
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d334473e326f28a628ebda9dede7a83340a1cb34
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3768"></a>编译器错误 C3768
不能将虚拟 vararg 函数的地址采用纯托管代码  
  
 **/Clr: pure**编译器选项在 Visual Studio 2015 中已弃用。  
  
 使用编译时`/clr:pure`，不能采用的虚拟地址`vararg`函数。  
  
## <a name="example"></a>示例  

 下面的示例生成 C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```
