---
title: 编译器错误 C3530 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6514d655ab813ae21ecb440415f87bce63f3591
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253513"
---
# <a name="compiler-error-c3530"></a>编译器错误 C3530
auto 不能与任何其他类型说明符组合  
  
 与使用的类型说明符`auto`关键字。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  请勿使用的变量声明中使用的类型说明符`auto`关键字。  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3530，因为变量`x`声明两个`auto`关键字和类型`int`，而使用编译该示例是因为 **/zc: auto**。  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)