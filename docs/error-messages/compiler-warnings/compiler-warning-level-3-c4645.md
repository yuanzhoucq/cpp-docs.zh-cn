---
title: 编译器警告 （等级 3） C4645 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718afb6b8336e36e0c0244cbdccd8af16ac4167f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292904"
---
# <a name="compiler-warning-level-3-c4645"></a>编译器警告（等级 3）C4645
用 __declspec(noreturn) 声明的函数有返回语句  
  
 A[返回](../../cpp/return-statement-in-program-termination-cpp.md)语句已将标有的函数中找到[noreturn](../../cpp/noreturn.md) `__declspec`修饰符。 忽略 `return` 语句。  
  
 下面的示例生成 C4645：  
  
```  
// C4645.cpp  
// compile with:  /W3  
void __declspec(noreturn) func() {  
   return;   // C4645, delete this line to resolve  
}  
  
int main() {  
}  
```