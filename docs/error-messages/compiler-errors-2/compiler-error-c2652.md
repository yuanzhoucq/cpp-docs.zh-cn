---
title: "编译器错误 C2652 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2652
dev_langs: C++
helpviewer_keywords: C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56cfdf52ec3a6947a6a82774f551fc1a6880c959
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2652"></a>编译器错误 C2652
identifier： 非法的复制构造函数： 第一个参数不能 identifier  
  
 复制构造函数中的第一个参数具有与类、 结构或联合为其定义相同的类型。 第一个参数可以是对的类型，但不是类型本身的引用。  
  
 下面的示例生成 C2651:  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```