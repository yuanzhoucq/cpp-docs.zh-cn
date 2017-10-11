---
title: "编译器错误 C2638 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2638
dev_langs:
- C++
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0f5eb7d56c715ade00d8aa4ca5c9e41a73441561
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2638"></a>编译器错误 C2638
identifier: __based 上指向成员的指针修饰符非法  
  
 `__based`修饰符不能使用指向成员的指针。  
  
 下面的示例生成 C2638:  
  
```  
// C2638.cpp  
void *a;  
  
class C {  
public:  
   int i;  
   int j;  
   int func();  
};  
int __based (a) C::* cpi = &C::i;  // C2638  
int (__based (a) C::* cpf)() = &C::func; // c2638  
```
