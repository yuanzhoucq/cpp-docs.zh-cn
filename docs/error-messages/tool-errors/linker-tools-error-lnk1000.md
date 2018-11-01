---
title: 链接器工具错误 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 8e53dc898addb4adeec63027c358b42a6a836b50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501720"
---
# <a name="linker-tools-error-lnk1000"></a>链接器工具错误 LNK1000

> 未知的错误;参考文档中的技术支持选项

请注意错误的情况下，然后尝试隔离问题并创建可重现的测试用例。 有关如何调查和报告这些错误的信息，请参阅[如何报告 Visual c + + 工具集或文档的问题](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果混合使用标准标头文件 (例如，Windows.h) 和您自己的文件，可能会收到此错误。 包括预编译标头，如果任何，第一个，然后标准标头后, 跟您自己的标头文件。