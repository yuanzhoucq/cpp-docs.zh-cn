---
title: "编译器错误 C2381 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0442b94b1151dbee006a0d3ee71b1076d7afe7df
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

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
