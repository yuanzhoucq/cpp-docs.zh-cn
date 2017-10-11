---
title: "编译器错误 C3641 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3641
dev_langs:
- C++
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 992e2a5d34b380146a99f6f78145b022eacd21d6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3641"></a>编译器错误 C3641
function： 无效的使用 /clr 编译的函数调用约定 calling_convention: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 仅[__clrcall](../../cpp/clrcall.md)调用约定允许使用[/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下面的示例生成 C3641:  
  
```  
// C3641.cpp  
// compile with: /clr:pure /c  
void __cdecl f() {}   // C3641  
```
