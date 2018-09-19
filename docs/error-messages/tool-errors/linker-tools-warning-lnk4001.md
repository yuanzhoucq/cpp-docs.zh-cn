---
title: 链接器工具警告 LNK4001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f684e85233c4df777a53f03f07936137c425946e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070414"
---
# <a name="linker-tools-warning-lnk4001"></a>链接器工具警告 LNK4001

未指定; 对象文件使用库

链接器传递一个或多个.lib 文件，但没有.obj 文件。

链接器不能访问它便可以访问在.obj 文件中的.lib 文件中的信息，因为此警告指示需要显式指定其他链接器选项。 例如，您可能需要指定[/机器](../../build/reference/machine-specify-target-platform.md)， [/out](../../build/reference/out-output-file-name.md)，或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)选项。