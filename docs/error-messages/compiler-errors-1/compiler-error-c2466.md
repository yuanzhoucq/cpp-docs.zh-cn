---
title: "编译器错误 C2466 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3c3ad19ce37aa51bd6b670da6e857d7eccce04ca
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2466"></a>编译器错误 C2466
无法分配常量大小为 0 的数组  
  
 分配或使用大小为零声明数组时。 数组大小的常量表达式必须是大于零的整数。 用零个下标的数组声明是合法，仅为类、 结构或联合成员，而且仅可与 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。  
  
 下面的示例生成 C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```
