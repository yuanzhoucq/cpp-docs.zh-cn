---
title: 编译器错误 C2719 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8779db363c506d2f4ad884e15f78ba8231caa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2719"></a>编译器错误 C2719
“parameter”：不对齐具有 __declspec(align('#')) 的形参  
  
 [对齐](../../cpp/align-cpp.md)`__declspec`函数参数中不允许修饰符。 函数参数的对齐方式由所使用的调用约定控制。 有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。  
  
 以下示例将生成 C2719，并演示如何修复此错误：  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```