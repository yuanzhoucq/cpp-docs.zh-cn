---
title: "编译器错误 C3530 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3530
dev_langs: C++
helpviewer_keywords: C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d66e76fc3e44a037f52aa6e217fae848f1338d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3530"></a>编译器错误 C3530
auto 不能与任何其他类型说明符组合  
  
 与使用的类型说明符`auto`关键字。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  请勿使用的变量声明中使用的类型说明符`auto`关键字。  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3530，因为变量`x`声明两个`auto`关键字和类型`int`，而使用编译该示例是因为**/zc: auto**。  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)