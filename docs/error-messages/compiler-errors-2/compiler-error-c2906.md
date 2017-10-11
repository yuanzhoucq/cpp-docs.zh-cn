---
title: "编译器错误 C2906 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2906
dev_langs:
- C++
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: da2806a0a945533fcc90e0a3d1045ff4f3c3b766
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2906"></a>编译器错误 C2906
“specialization”: 显式专用化需要“template <>”  
  
 有关模板的显式专用化，必须使用新的语法。  
  
 下面的示例生成 C2906:  
  
```  
// C2906.cpp  
// compile with: /c  
template<class T> class X{};   // primary template  
class X<int> { }   // C2906  
template<> class X<int> { };   // new syntax  
```
