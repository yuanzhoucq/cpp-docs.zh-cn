---
title: 编译器错误 C2351 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2351
dev_langs:
- C++
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1660e5dfc4f17f7617c82eb3e633f345e2774495
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222376"
---
# <a name="compiler-error-c2351"></a>编译器错误 C2351
已过时的 c + + 构造函数初始化语法  
  
 在新样式初始化列表中的构造函数，必须显式命名每个直接的基类，即使它是唯一的基类。  
  
 下面的示例生成 C2351:  
  
```  
// C2351.cpp  
// compile with: /c  
class B {  
public:   
   B() : () {}   // C2351  
   B() {}   // OK  
};  
```