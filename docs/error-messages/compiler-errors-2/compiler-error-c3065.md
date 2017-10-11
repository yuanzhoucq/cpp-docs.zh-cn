---
title: "编译器错误 C3065 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3065
dev_langs:
- C++
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 059493df3a2c805e829bb50311b2fadebbbc575b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3065"></a>编译器错误 C3065
不允许在非类范围上声明属性  
  
 在类的外部使用了 [property](../../cpp/property-cpp.md) __declspec 修饰符。  只能在类内部声明属性。  
  
 以下示例生成 C3065：  
  
```  
// C3065.cpp  
// compile with: /c  
__declspec(property(get=get_i)) int i;   // C3065  
  
class x {  
public:  
   __declspec(property(get=get_i)) int i;   // OK  
};  
```
