---
title: "编译器错误 C2537 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 610fe53b68ccfa9f0ec187356a737e67837656a4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2537"></a>编译器错误 C2537
specifier： 非法链接规范  
  
 可能的原因：  
  
1.  不支持链接说明符。 支持"C"的链接说明符。  
  
2.  对于重载函数的一组中的多个函数指定了"C"链接。 这是不允许的。  
  
 下面的示例生成 C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```
