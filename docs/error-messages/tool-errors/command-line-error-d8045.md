---
title: 命令行错误 D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214190"
---
# <a name="command-line-error-d8045"></a>命令行错误 D8045

不能编译 C 文件 file 与 /clr 选项

仅C++源代码文件可以传递给使用的编译 **/clr**。  使用 **/TP**以.c 文件编译为.cpp 文件; 请参阅[/Tc、 /Tp、 /TC、 /TP （指定源文件类型）](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)有关详细信息。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

如果编译 ATL 应用程序使用视觉对象也会发生 D8045 C++。 请参阅[如何：迁移到 /clr](../../dotnet/how-to-migrate-to-clr.md)有关详细信息。