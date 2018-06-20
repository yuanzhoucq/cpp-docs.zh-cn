---
title: 链接器工具错误 LNK1000 |Microsoft 文档
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238677"
---
# <a name="linker-tools-error-lnk1000"></a>链接器工具错误 LNK1000

> 未知的错误;请查阅文档以技术支持选项

注意错误的情况，然后尝试隔离问题并创建可重现的测试用例。 有关如何调查并报告这些错误的信息，请参阅[如何报告使用 Visual c + + 工具集或文档的问题](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果混合使用标准头文件 (例如，Windows.h) 和你自己的文件，则可能出现此错误。 包括预编译标头，如果任何，第一个，然后标准标头后, 跟你自己的标头文件。