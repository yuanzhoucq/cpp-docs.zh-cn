---
title: "编译器错误 C2437 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2437
dev_langs: C++
helpviewer_keywords: C2437
ms.assetid: 2d2b3c6c-856a-4b27-ae10-64813b3e5483
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4a46df9cbf497f0e71ee5b0ec8d21ee226ca21b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2437"></a>编译器错误 C2437
identifier： 已初始化  
  
 一个对象只能初始化一次。  
  
 下面的示例生成 C2437:  
  
```  
// C2437.cpp  
// compile with: /c  
class A {  
public:  
   A(int i) {}  
};  
  
class B : A {  
   B() : A(1), A(2) {}   // C2437  
   B() : A(1) {}   // OK  
};  
```