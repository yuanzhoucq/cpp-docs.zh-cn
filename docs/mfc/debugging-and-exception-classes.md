---
title: 调试和异常类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 328d7a38c544b56f83ea3e8b1136b1122c4dfa14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241156"
---
# <a name="debugging-and-exception-classes"></a>调试和异常类

这些类为调试动态内存分配和将异常信息从引发异常的函数传递到捕获异常的函数提供支持。

使用类[CDumpContext](../mfc/reference/cdumpcontext-class.md)并[CMemoryState](../mfc/reference/cmemorystate-structure.md)开发以帮助调试，如中所述过程[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)在运行时确定的任何对象类，如本文所述[访问运行时类信息](../mfc/accessing-run-time-class-information.md)。 框架使用 `CRuntimeClass` 动态创建特定类的对象。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
