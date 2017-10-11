---
title: "编译器错误 C2574 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2574
dev_langs:
- C++
helpviewer_keywords:
- C2574
ms.assetid: 3e1c5c18-ee8b-4dbb-bfc0-d3b8991af71b
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 31e6b1c7dc2e2a1fcb0a04e284d0251e59ebb8bd
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2574"></a>编译器错误 C2574
析构函数： 不能声明为静态  
  
 可以声明析构函数和构造函数都不`static`。  
  
 下面的示例生成 C2574:  
  
```  
// C2574.cpp  
// compile with: /c  
class A {  
   virtual static ~A();   // C2574  
   //  try the following line instead  
   // virtual ~A();  
};  
```
