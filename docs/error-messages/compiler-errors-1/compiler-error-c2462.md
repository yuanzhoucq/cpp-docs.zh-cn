---
title: 编译器错误 C2462 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4ce82ed15bdb8844f69abc260446c1af2fd4a0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2462"></a>编译器错误 C2462
identifier： 无法在新的表达式中定义的类型  
  
 不能定义一种类型的操作数字段中`new`运算符。 将类型定义放入单独的语句。  
  
 下面的示例生成 C2462:  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```