---
title: "编译器错误 C3533 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3533
dev_langs: C++
helpviewer_keywords: C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7bcd9c710ac5cdd50b966a72291918459d984be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533
type: 参数不能具有包含 auto 的类型  
  
 方法或模板的参数不能用声明`auto`关键字如果默认值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项将生效。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  删除`auto`从参数声明的关键字。  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3535，因为它声明的函数参数`auto`关键字和它进行编译的**/zc: auto**。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3535，因为它声明的模板参数`auto`关键字和它进行编译的**/zc: auto**。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)