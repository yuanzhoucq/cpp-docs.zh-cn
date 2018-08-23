---
title: 编译器错误 C2381 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd5f5edcf95144333524c41b803c24b728a621f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225272"
---
# <a name="compiler-error-c2381"></a>编译器错误 C2381
function： 重定义;__declspec （noreturn） 不同  
  
 声明函数并将其所使用的定义但然后定义[noreturn](../../cpp/noreturn.md) `__declspec`修饰符。 使用`noreturn`构成该函数的重定义; 的声明和定义需要使用上达成一致`noreturn`。  
  
 下面的示例生成 C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```