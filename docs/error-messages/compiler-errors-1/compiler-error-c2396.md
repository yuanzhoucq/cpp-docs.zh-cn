---
title: "编译器错误 C2396 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20eca11d402265bbc81d61a8079ae9975cceef67
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2396"></a>编译器错误 C2396
operator'type ': CLR 或 WinRT 用户定义的转换 functionnot 有效。 必须转换自或转换至：“T^”、“T^%”、“T^&”，其中 T =“your_type”  
  
 Windows 运行时或托管类型中的转换函数没有至少一个类型与包含转换函数的类型相同的参数。  
  
 下面的示例生成 C2396，并演示如何修复此错误：  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```
