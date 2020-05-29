---
title: 链接器工具错误 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195417"
---
# <a name="linker-tools-error-lnk1000"></a>链接器工具错误 LNK1000

> 未知错误;有关技术支持选项，请参阅文档

请注意错误的情况，然后尝试隔离问题并创建可重现的测试用例。 有关如何调查和报告这些错误的信息，请参阅[如何报告 Visual C++工具集或文档的问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果混合使用标准头文件（例如，Windows .h）和自己的文件，可能会收到此错误。 首先包含预编译标头（如果有），然后是标准标头，然后是您自己的标头文件。
