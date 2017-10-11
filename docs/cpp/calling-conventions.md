---
title: "调用约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: bbdee0427dcefc019214e7f9af16831f162cef83
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="calling-conventions"></a>调用约定
Visual C/C++ 编译器提供了用于调用内部函数和外部函数的几个不同的约定。 了解这些不同的方法有助于调试程序以及将您的代码与汇编语言例程链接。  
  
 本主题中的各个主题说明了调用约定之间的差异、如何传递参数以及函数如何返回值。 它们也讨论了裸函数调用以及使您能够写入自己的 prolog 和 epilog 代码的高级功能。  
  
 有关信息的 x64 调用约定处理器，请参阅[调用约定](../build/calling-convention.md)。  
  
## <a name="topics-in-this-section"></a>本节中的主题  
  
-   [自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)(`__cdecl`， `__stdcall`， `__fastcall`，等)  
  
-   [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [使用裸函数调用编写自定义 prolog/epilog 代码](../cpp/naked-function-calls.md)  
  
-   [浮点协处理器和调用约定](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [已过时调用约定](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)
