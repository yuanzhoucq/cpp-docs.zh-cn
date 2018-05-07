---
title: 编译器错误 C2379 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1016bedfa9df0e9dfacb56734ee60397108d046
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2379"></a>编译器错误 C2379
形参数有不同的类型提升时  
  
 指定的参数的类型不兼容，通过默认提升，与以前的声明中的类型。 这是 ANSI C 中的错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和警告具有 Microsoft 扩展 (**/Ze**)。  
  
 下面的示例生成 C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```