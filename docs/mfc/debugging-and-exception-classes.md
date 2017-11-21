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
ms.openlocfilehash: 9fb3da38c9a17ae84c42d1a2337059a3932cbf04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="debugging-and-exception-classes"></a>调试和异常类
这些类为调试动态内存分配和将异常信息从引发异常的函数传递到捕获异常的函数提供支持。  
  
 使用类[CDumpContext](../mfc/reference/cdumpcontext-class.md)和[CMemoryState](../mfc/reference/cmemorystate-structure.md)在开发以帮助调试中, 所述过程[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)在运行时确定的任何对象类，如文所述[访问运行时类信息](../mfc/accessing-run-time-class-information.md)。 框架使用 `CRuntimeClass` 动态创建特定类的对象。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../mfc/class-library-overview.md)

