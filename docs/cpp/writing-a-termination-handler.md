---
title: 编写终止处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85241d9dde87e929b02328a6e7d0c75b5ce068ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116225"
---
# <a name="writing-a-termination-handler"></a>编写终止处理程序

与异常处理程序不同，无论代码的受保护块是否已正常终止，终止处理程序总是会执行。 终止处理程序的唯一用途应该是确保无论代码的节如何完成执行，内存、句柄和文件等资源都能正确关闭。

终止处理程序使用 try-finally 语句。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [Try-finally 语句](../cpp/try-finally-statement.md)

- [清理资源](../cpp/cleaning-up-resources.md)

- [异常处理中的操作的执行时间](../cpp/timing-of-exception-handling-a-summary.md)

- [终止处理程序的限制](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>请参阅

[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)