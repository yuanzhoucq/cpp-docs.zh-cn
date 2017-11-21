---
title: "编译器错误 C2719 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2719
dev_langs: C++
helpviewer_keywords: C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7e6707dfd5666cb8852e3bbf59cf7a81dd24766
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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