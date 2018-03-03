---
title: "编译器错误 C2719 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 554a8c2655e82e7d793966738474338aab934168
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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