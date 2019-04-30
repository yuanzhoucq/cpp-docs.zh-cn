---
title: 链接器工具警告 LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395074"
---
# <a name="linker-tools-warning-lnk4206"></a>链接器工具警告 LNK4206

> 找不到; 预编译的类型信息'*文件名*不链接或重写; 正在链接对象，如同没有调试信息一样

*文件名*通过使用编译的对象文件[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 LINK 命令中既未指定或已被覆盖。

此警告的常见方案是用 /Yc 编译.obj 时在库中，并有没有对该.obj 在代码中的符号引用。  在这种情况下，链接器将不使用 （或甚至看到）.obj 文件。  在此情况下，应重新编译代码并将[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)使用编译的对象[/Yu](../../build/reference/yu-use-precompiled-header-file.md)。