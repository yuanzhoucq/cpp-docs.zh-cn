---
title: 命令行错误 D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 05a2d3851e58062e1e326781a223e2f4b0346620
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196841"
---
# <a name="command-line-error-d8045"></a>命令行错误 D8045

无法用/clr 选项编译 C 文件 "file"

只有C++源代码文件才能传递到使用 **/clr**的编译。  使用 **/tp**将 .c 文件编译为 .cpp 文件;有关详细信息，请参阅[/tc、/tp、/tc、/tp （指定源文件类型）](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

如果使用视觉对象C++编译 ATL 应用程序，也可能会发生 D8045。 有关详细信息，请参阅[如何：迁移到/clr](../../dotnet/how-to-migrate-to-clr.md) 。
