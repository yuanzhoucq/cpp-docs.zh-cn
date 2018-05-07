---
title: 编译器错误 C2062 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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