---
title: 错误 C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 4ab96c0516ee5593a969669c03ae22f0c211ae27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208578"
---
# <a name="fatal-error-c1383"></a>错误 C1383

编译器选项 /GL 与安装的公共语言运行时版本不兼容

将以前版本的公共语言运行时与较新编译器结合使用时，以及使用 **/clr** 和 **/GL.** 进行编译时，会发生 C1383。

要进行解决，请勿将 **/GL** 与 **/clr** 结合使用，或是安装随你的编译器附带的公共语言运行时版本。

有关详细信息，请参阅 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 和 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。