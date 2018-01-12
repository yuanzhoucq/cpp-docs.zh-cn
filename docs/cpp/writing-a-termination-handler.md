---
title: "编写终止处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9d4099a7f40acf0b5bfcc89f1c95cb880683b86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="writing-a-termination-handler"></a>编写终止处理程序
与异常处理程序不同，无论代码的受保护块是否已正常终止，终止处理程序总是会执行。 终止处理程序的唯一用途应该是确保无论代码的节如何完成执行，内存、句柄和文件等资源都能正确关闭。  
  
 终止处理程序使用 try-finally 语句。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [Try-finally 语句](../cpp/try-finally-statement.md)  
  
-   [清理资源](../cpp/cleaning-up-resources.md)  
  
-   [操作的异常处理计时](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [对于终止处理程序的限制](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>请参阅  
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)