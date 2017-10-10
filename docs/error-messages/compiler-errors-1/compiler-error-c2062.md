---
title: "编译器错误 C2062 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 775923345052aba99b05f708c417b8bed267119b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2062"></a>编译器错误 C2062
类型 type 意外  
  
 编译器意料之外的类型名称。  
  
 下面的示例生成 C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 C2062 也可能发生的方式编译器由于句柄构造函数的参数列表中未定义的类型。 如果编译器遇到了未定义的 （拼写错误？） 类型，则假定该构造函数是一个表达式，并发出 C2062。 若要解决，只能在构造函数参数列表中使用定义的类型。
