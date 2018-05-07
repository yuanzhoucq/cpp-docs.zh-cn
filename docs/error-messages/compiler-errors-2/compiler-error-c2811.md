---
title: 编译器错误 C2811 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2811
dev_langs:
- C++
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef9c608f19be28dbbeeca89c5f6672149e0ac4f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2811"></a>编译器错误 C2811
type1： 不能继承自 type2，ref 类只能继承自 ref 类或接口类  
  
 你尝试使用非托管的类用作基类的托管类。  
  
 下面的示例生成 C2811:  
  
```  
// C2811.cpp  
// compile with: /clr /c  
struct S{};  
ref struct T {};  
ref class C : public S {};   // C2811  
ref class D : public T {};   // OK  
```