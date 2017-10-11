---
title: "编译器错误 C3923 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3923
dev_langs:
- C++
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 863273ec0e9922a6a0b4e7355fe47178a7dd5bbe
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3923"></a>编译器错误 C3923
“member”：不允许在 WinRT 或托管类的成员函数中使用局部类、结构或联合定义  
  
## <a name="example"></a>示例  
 下列示例生成 C3923。  
  
```  
// C3923.cpp  
// compile with: /clr /c  
ref struct x {  
   void Test() {  
      struct a {};   // C3923  
      class b {};   // C3923  
      union c {};   // C3923  
   }  
};  
```
