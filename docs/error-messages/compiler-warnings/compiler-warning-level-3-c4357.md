---
title: 编译器警告 （等级 3） C4357 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4357
dev_langs:
- C++
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79bb609b051def4f84924c1d9ebbcd9574d2ce77
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289667"
---
# <a name="compiler-warning-level-3-c4357"></a>编译器警告（等级 3）C4357
param 数组自变量形式自变量列表中的委托 del 忽略时生成 function  
  
 `ParamArray`属性将被忽略，和`function`不能使用变量自变量调用。  
  
 下面的示例生成 C4357:  
  
```  
// C4357.cpp  
// compile with: /clr /W3 /c  
using namespace System;  
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357  
  
public delegate void g(int i, array<Object^>^ varargs);   // OK  
```