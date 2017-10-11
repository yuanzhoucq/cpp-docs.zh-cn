---
title: "编译器错误 C3163 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 95fb254036d2883b6efe6b81bda54864d533c2a8
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3163"></a>编译器错误 C3163
construct： 属性与以前的声明不一致  
  
 应用于定义的属性应用于声明的属性与发生冲突。  
  
 若要解决 C3163 的一种方法是消除前向声明上的属性。 前向声明的任何属性都应小于在定义的属性，或最多，等于到它们。  
  
 C3163 错误的可能原因包括 Microsoft 源代码注释语言 (SAL)。 除非使用编译你的项目，否则 SAL 宏不展开**/ 分析**标志。 如果你尝试重新编译使用，而无需完全编译 / 分析的程序可能会引发 C3163 / 分析选项。 有关 SAL 的详细信息，请参阅[SAL 批注](../../c-runtime-library/sal-annotations.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3163。  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>另请参阅  
 [SAL 批注](../../c-runtime-library/sal-annotations.md)
