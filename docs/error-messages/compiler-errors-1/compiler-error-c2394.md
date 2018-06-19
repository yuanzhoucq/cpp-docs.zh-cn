---
title: 编译器错误 C2394 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2394
dev_langs:
- C++
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a31a43e50a19765d7d5a07ca61f3195099793ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197736"
---
# <a name="compiler-error-c2394"></a>编译器错误 C2394
your_type:: operator'op'": CLR 或 WinRToperator 无效。 至少一个参数必须是以下类型：“T^”、“T^%”、“T^&”，其中 T =“your_type”  
  
 Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。  
  
 以下示例生成 C2394：  
  
```  
// C2394.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y^ operator -(int i, char c);   // C2394  
  
   // OK  
   static Y^ operator -(Y^ hY, char c);  
   // or  
   static Y^ operator -(int i, Y^& rhY);  
};  
```