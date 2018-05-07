---
title: 编译器错误 C3533 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f184f0459e7ec2251d6ff34e2ee76559fe0dea42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533
type: 参数不能具有包含 auto 的类型  
  
 方法或模板的参数不能用声明`auto`关键字如果默认值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项将生效。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  删除`auto`从参数声明的关键字。  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3535，因为它声明的函数参数`auto`关键字和它进行编译的 **/zc: auto**。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3535，因为它声明的模板参数`auto`关键字和它进行编译的 **/zc: auto**。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)