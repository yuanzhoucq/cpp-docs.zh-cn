---
title: 调试和异常类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7c88c5d12f56318bbb37a825e28c2bfcbc132d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418172"
---
# <a name="debugging-and-exception-classes"></a>调试和异常类

这些类为调试动态内存分配和将异常信息从引发异常的函数传递到捕获异常的函数提供支持。

使用类[CDumpContext](../mfc/reference/cdumpcontext-class.md)并[CMemoryState](../mfc/reference/cmemorystate-structure.md)开发以帮助调试，如中所述过程[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)在运行时确定的任何对象类，如本文所述[访问运行时类信息](../mfc/accessing-run-time-class-information.md)。 框架使用 `CRuntimeClass` 动态创建特定类的对象。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

