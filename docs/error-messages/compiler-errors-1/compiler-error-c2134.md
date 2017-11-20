---
title: "编译器错误 C2134 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2134
dev_langs: C++
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 380a26192b907100f3257b4ca9ee66395f18c2c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2134"></a>编译器错误 C2134
function： 调用不会导致常量表达式  
  
 声明为 constexpr 只能调用其他函数的函数声明为 constexpr。  
  
 下面的示例生成 C2134:  
  
```  
// C2134.cpp  
// compile with: /c  
int A() {  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // Error C2134: 'A': call does not result in a constant expression.  
}  
```  
  
 可能的解决方法：  
  
```  
// C2134b.cpp  
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // No error  
}  
```