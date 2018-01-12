---
title: "编译器错误 C2770 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2770
dev_langs: C++
helpviewer_keywords: C2770
ms.assetid: 100001b5-80b0-4971-8ff6-9023f443c926
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1a8abc2f295db7acb195b2f837d96f1e53d9fbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2770"></a>编译器错误 C2770
template 的无效显式 template_or_generic 参数  
  
 使用显式模板或泛型自变量的函数模板候选项时不允许的函数类型。  
  
 下面的示例生成 C2770:  
  
```  
// C2770.cpp  
#include <stdio.h>  
template <class T>  
int f(typename T::B*);   // expects type with member B  
  
struct Err {};  
  
int main() {  
   f<int>(0);   // C2770 int has no B  
   // try the following line instead  
   f<OK>(0);  
}  
```