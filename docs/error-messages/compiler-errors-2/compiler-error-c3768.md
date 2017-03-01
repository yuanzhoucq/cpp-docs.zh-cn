---
title: "编译器错误 C3768 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: cb9c1c3a41deb35e6aa82d3d77e61dfd4b15a7cb
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3768"></a>编译器错误 C3768
在纯托管代码中不能采用虚拟 vararg 函数的地址  
  
 **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 使用编译时`/clr:pure`，您无法采用的一个虚拟地址`vararg`函数。  
  
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
