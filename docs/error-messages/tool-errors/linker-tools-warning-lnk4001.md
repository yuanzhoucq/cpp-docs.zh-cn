---
title: 链接器工具警告 LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194403"
---
# <a name="linker-tools-warning-lnk4001"></a>链接器工具警告 LNK4001

未指定对象文件;使用的库

链接器传递了一个或多个 .lib 文件，但没有 .obj 文件。

由于链接器无法访问其能够在 .obj 文件中访问的 .lib 文件中的信息，因此此警告表明您必须显式指定其他链接器选项。 例如，你可能需要指定[/MACHINE](../../build/reference/machine-specify-target-platform.md)、 [/out](../../build/reference/out-output-file-name.md)或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)选项。
