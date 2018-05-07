---
title: 编译器警告 （等级 4） C4242 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4242
dev_langs:
- C++
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: befe02b363c17a670d3b33632ffa50ed8a7cb1f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4242"></a>编译器警告（等级 4）C4242
identifier： 从 type1 到 type2，可能丢失数据的转换  
  
 类型是不同的。 类型转换可能会导致数据丢失。 编译器进行类型转换。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 C4242 的其他信息，请参阅[常见编译器错误](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 下面的示例生成 C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```