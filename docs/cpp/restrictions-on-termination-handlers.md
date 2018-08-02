---
title: 终止处理程序的限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae16363956afc7cca853307ef2888846a02864d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461765"
---
# <a name="restrictions-on-termination-handlers"></a>对于终止处理程序的限制
不能使用**goto**语句跳转到 **__try**语句块或 **__finally**语句块。 相反，您必须通过常规控制流进入此语句块。 (您可以但是，跳转出 **__try**语句块。)此外，不能嵌套异常处理程序或终止处理程序 **__finally**块。  
  
 此外，终止处理程序中允许的某些类型的代码会生成有问题的结果，因此你应小心使用它们（如果要使用）。 一个是**goto**语句跳出 **__finally**语句块。 如果该块正在作为正常终止的一部分执行，则不会发生任何异常。 但如果系统正在展开堆栈，则该展开会停止，并且当前函数会获取控制权，就象异常终止不存在一样。  
  
 一个**返回**内的语句 **__finally**语句块存在大致相同这种情况。 控制权将返回给包含终止处理程序的函数的直接调用方。 如果系统正在展开堆栈，此进程将暂停，如果没有引发过异常，则程序将继续执行。  
  
## <a name="see-also"></a>请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)