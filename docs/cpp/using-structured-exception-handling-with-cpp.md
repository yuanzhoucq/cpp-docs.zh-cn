---
title: 将结构化的异常处理用于 C++ |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5d067a391512d56a2d01ce3052ac3fab061f28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-structured-exception-handling-with-c"></a>将结构化异常处理用于 C++
这些文章中描述的结构化异常处理适用于 C 和 C++ 源文件。 但是，这不是专门针对 C++ 设计，因此不建议使用。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理机制更灵活，因为它可以处理任何类型的异常。  
  
 Microsoft C++ 现在支持基于 ANSI C++ 标准的 C++ 异常处理模型。 此机制将自动处理堆栈展开过程中的本地对象的析构。 如果要编写容错的 C++ 代码，并且要实现异常处理，则强烈建议使用 C++ 异常处理，而不是结构化异常处理。 （请注意，尽管 C++ 编译器支持这些文章中所述的结构化异常处理构造，但标准 C 编译器不支持 C++ 异常处理语法。）有关 c + + 异常处理的详细信息，请参阅[C++ 异常处理](../cpp/cpp-exception-handling.md)和*C++ 参考手册批注 》* Margaret Ellis 和 Bjarne stroustrup 撰写。  
  
## <a name="see-also"></a>请参阅  
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)