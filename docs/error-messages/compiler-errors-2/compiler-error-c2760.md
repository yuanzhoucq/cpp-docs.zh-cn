---
title: "编译器错误 C2760 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2760
dev_langs: C++
helpviewer_keywords: C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02174986138190a03db2211eb6f67e0626261091
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2760"></a>编译器错误 C2760
语法错误： 预期 name1 不 name2  
  
 强制转换运算符用于无效的运算符。  
  
 下面的示例生成 C2760:  
  
```  
// C2760.cpp  
class B {};  
class D : public B {};  
  
void f(B* pb) {  
    D* pd1 = static_cast<D*>(pb);  
    D* pd2 = static_cast<D*>=(pb);  // C2760  
    D* pd3 = static_cast<D*=(pb);   // C2760  
}  
```