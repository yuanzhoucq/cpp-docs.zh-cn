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
ms.openlocfilehash: faaf53d08512559b86c95148bc93e7b3367d2b01
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458909"
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533
type: 参数不能具有包含 auto 的类型  
  
 方法或模板的参数不能用声明`auto`关键字如果默认值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项将生效。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  删除`auto`从参数声明的关键字。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3533，因为它声明的函数参数`auto`关键字和它进行编译的 **/zc: auto**。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j) {} // C3533  
```  
  
## <a name="example"></a>示例  
 下面的示例在 C + + 14 模式下生成 C3533，因为它声明的模板参数`auto`关键字和它进行编译的 **/zc: auto**。（在 C + + 17，这是具有单个非类型模板参数推导其类型的类模板的有效定义。）
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C {}; // C3533  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)
