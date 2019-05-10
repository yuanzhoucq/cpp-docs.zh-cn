---
title: 链接器工具错误 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: b0e6eb3ba44216e9300506eb84adb61a6529903d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255453"
---
# <a name="linker-tools-error-lnk1000"></a>链接器工具错误 LNK1000

> 未知的错误;参考文档中的技术支持选项

请注意错误的情况下，然后尝试隔离问题并创建可重现的测试用例。 有关如何调查和报告这些错误的信息，请参阅[如何报告问题与视觉对象C++工具集或文档](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果混合使用标准标头文件 (例如，Windows.h) 和您自己的文件，可能会收到此错误。 包括预编译标头，如果任何，第一个，然后标准标头后, 跟您自己的标头文件。