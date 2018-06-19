---
title: 编译器错误 C2533 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06733dc8ee52462ab7fcac4255ee8fa697a9bac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229661"
---
# <a name="compiler-error-c2533"></a>编译器错误 C2533
“identifier”: 构造函数不能有返回类型  
  
 构造函数不能具有返回类型（甚至不能是 `void` 返回类型）。  
  
 此错误的常见来源是类定义结尾与第一个构造函数实现之间缺少分号。 编译器会将类视为构造函数返回类型的定义，会生成 C2533。  
  
 下面的示例生成 C2533，并演示如何修复此错误：  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```