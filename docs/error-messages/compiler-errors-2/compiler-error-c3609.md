---
title: "编译器错误 C3609 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3609
dev_langs:
- C++
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: eb5d5127020ad1855c3fe7d94c362deeee53ccad
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3609"></a>编译器错误 C3609
“成员”：密封的或最终函数必须是虚拟函数  
  
 [密封](../../windows/sealed-cpp-component-extensions.md)和[最终](../../cpp/final-specifier.md)关键字标记的类、 结构或成员函数上只允许`virtual`。  
  
 以下示例生成 C3609：  
  
```  
// C3609.cpp  
// compile with: /clr /c  
ref class C {  
   int f() sealed;   // C3609  
   virtual int f2() sealed;   // OK  
};  
```  

