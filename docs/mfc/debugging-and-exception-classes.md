---
title: "调试和异常类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.debug
dev_langs: C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 622e6d04a567668ebfd2c737c5cdde1c2ea09b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-exception-classes"></a>调试和异常类
这些类为调试动态内存分配和将异常信息从引发异常的函数传递到捕获异常的函数提供支持。  
  
 使用类[CDumpContext](../mfc/reference/cdumpcontext-class.md)和[CMemoryState](../mfc/reference/cmemorystate-structure.md)在开发以帮助调试中, 所述过程[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)在运行时确定的任何对象类，如文所述[访问运行时类信息](../mfc/accessing-run-time-class-information.md)。 框架使用 `CRuntimeClass` 动态创建特定类的对象。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

