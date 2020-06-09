---
title: 调试和异常类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 6c7d1fc20556993c3c6690122786d7a767d895ad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625941"
---
# <a name="debugging-and-exception-classes"></a>调试和异常类

这些类为调试动态内存分配和将异常信息从引发异常的函数传递到捕获异常的函数提供支持。

在开发过程中使用类[CDumpContext](reference/cdumpcontext-class.md)和[CMemoryState](reference/cmemorystate-structure.md)来协助调试，如[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)中所述。 在运行时使用[CRuntimeClass](reference/cruntimeclass-structure.md)来确定任何对象的类，如[访问运行时类信息](accessing-run-time-class-information.md)一文中所述。 框架使用 `CRuntimeClass` 动态创建特定类的对象。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
