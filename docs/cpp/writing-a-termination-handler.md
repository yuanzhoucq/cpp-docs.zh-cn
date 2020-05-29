---
title: 编写终止处理程序
ms.date: 11/04/2016
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
ms.openlocfilehash: 8a243281e0d984a42cd4b4d9f249d867812d8bca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187305"
---
# <a name="writing-a-termination-handler"></a>编写终止处理程序

与异常处理程序不同，无论代码的受保护块是否已正常终止，终止处理程序总是会执行。 终止处理程序的唯一用途应该是确保无论代码的节如何完成执行，内存、句柄和文件等资源都能正确关闭。

终止处理程序使用 try-finally 语句。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [Try-catch 语句](../cpp/try-finally-statement.md)

- [清理资源](../cpp/cleaning-up-resources.md)

- [异常处理中的操作时间](../cpp/timing-of-exception-handling-a-summary.md)

- [终止处理程序的限制](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>另请参阅

[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
