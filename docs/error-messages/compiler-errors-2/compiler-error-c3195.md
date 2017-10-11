---
title: "编译器错误 C3195 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e6e95ce1592c98fae59869e0153ee27c0f727397
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3195"></a>编译器错误 C3195
“operator”: 被保留并且不能用作 ref 类或值类型的成员。 必须使用“operator”关键字定义 CLR 或 WinRT 运算符  
  
编译器检测到了使用 C++ 托管扩展语法的运算符定义。 为运算符，必须使用 c + + 语法。  
  
下面的示例生成 C3195，并演示如何修复此错误：  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```
