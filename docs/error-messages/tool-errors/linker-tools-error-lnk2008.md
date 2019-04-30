---
title: 链接器工具错误 LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386520"
---
# <a name="linker-tools-error-lnk2008"></a>链接器工具错误 LNK2008

链接地址信息目标不是对齐 symbol_name

在没有正确对齐的对象文件中找到链接地址信息目标链接。

此错误可能由自定义 secton 对齐方式 (例如，#pragma [pack](../../preprocessor/pack.md))，[对齐](../../cpp/align-cpp.md)修饰符，或通过修改 secton 对齐方式的程序集语言代码。

如果你的代码不使用上述任一操作，这可能被引起编译器。