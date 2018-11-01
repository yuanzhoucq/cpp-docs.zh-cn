---
title: 错误 C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: feb385161c9bc13d89052b4947174fbdce7a0d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457377"
---
# <a name="fatal-error-c1854"></a>错误 C1854

> 无法覆盖创建对象文件中的预编译头期间生成的信息:*文件名*

您指定[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)选项后指定[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)相同文件的选项。

若要解决此问题，一般情况下，只有一个文件中设置你的项目以使用编译 **/Yc**选项，并设置所有其他文件来通过编译 **/Yu**选项。 有关使用的详细信息 **/Yc**选项，以及如何在 Visual Studio IDE 中进行设置，请参阅[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)。 使用预编译标头的详细信息，请参阅[创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)。
