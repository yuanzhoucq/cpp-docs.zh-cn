---
title: "编译器错误 C2838 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2838
dev_langs: C++
helpviewer_keywords: C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 75f6cdae94cd1be386fbe6af2cc492404162d0d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2838"></a>编译器错误 C2838
member： 非法的限定的名称，在成员声明  
  
 类、 结构或联合使用完全限定的名称重新声明另一个类、 结构或联合的成员。  
  
 下面的示例生成 C2838:  
  
```  
// C2838.cpp  
// compile with: /c  
class Bellini {  
public:  
    void Norma();  
};  
  
class Bottesini {  
   Bellini::Norma();  // C2838  
};  
```