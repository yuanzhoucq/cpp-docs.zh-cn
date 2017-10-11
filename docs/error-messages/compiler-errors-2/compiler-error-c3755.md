---
title: "编译器错误 C3755 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3755
dev_langs:
- C++
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c302a3a0a417b8668d18c8329b083648cb28ccab
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3755"></a>编译器错误 C3755
delegate： 不能定义委托  
  
 A[委托 （c + + 组件扩展）](../../windows/delegate-cpp-component-extensions.md)可以声明但未定义。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3755。  
  
```  
// C3755.cpp  
// compile with: /clr /c  
delegate void MyDel() {};   // C3755  
```  
  
## <a name="example"></a>示例  
 如果你尝试创建委托模板，也会发生 C3755。 下面的示例生成 C3755。  
  
```  
// C3755_b.cpp  
// compile with: /clr /c  
ref struct R {  
   template<class T>  
   delegate void D(int) {}   // C3755  
};  
```
