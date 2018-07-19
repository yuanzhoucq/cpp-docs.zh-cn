---
title: 调用约定 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9e65dfd7f7cff25debd8eb0d00a7e3bb0397692
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410887"
---
# <a name="calling-conventions"></a>调用约定
Visual C/C++ 编译器提供了用于调用内部函数和外部函数的几个不同的约定。 了解这些不同的方法有助于调试程序以及将你的代码与汇编语言例程链接。  
  
 本主题中的各个主题说明了调用约定之间的差异、如何传递参数以及函数如何返回值。 它们也讨论了裸函数调用以及使你能够写入自己的 prolog 和 epilog 代码的高级功能。  
  
 有关信息的 x64 调用约定处理器，请参阅[调用约定](../build/calling-convention.md)。  
  
## <a name="topics-in-this-section"></a>本节中的主题  
  
-   [自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)(`__cdecl`， `__stdcall`， `__fastcall`，等)  
  
-   [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [使用裸函数调用编写自定义 prolog/epilog 代码](../cpp/naked-function-calls.md)  
  
-   [浮点协处理器和调用约定](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [已过时调用约定](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>请参阅  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)