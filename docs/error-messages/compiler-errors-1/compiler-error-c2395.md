---
title: 编译器错误 C2395 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 411a8d62de801591ff6a90a7bf74f3b2cfe67c7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225421"
---
# <a name="compiler-error-c2395"></a>编译器错误 C2395
“your_type::operator'op'”：CLR 或 WinRT 运算符无效。 至少一个参数必须是以下类型：“T”、“T%”、“T&”、“T^”、“T^%”、“T^&”，其中 T =“your_type”  
  
 Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。  
  
 下面的示例生成 C2395，并演示如何修复此错误：  
  
```  
// C2395.cpp  
// compile with: /clr /c  
value struct V {  
   static V operator *(int i, char c);   // C2395  
  
   // OK  
   static V operator *(V v, char c);  
   // or  
   static V operator *(int i, V& rv);  
};  
```