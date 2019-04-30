---
title: 编译器错误 C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400326"
---
# <a name="compiler-error-c3505"></a>编译器错误 C3505

> 无法加载类型库*guid*

如果运行 32 位、 x86 承载交叉编译器针对 64 位，可能会导致 C3505，x64 上 64 位目标计算机，因为编译器在 WOW64 下运行，并且只能读取 32 位注册表配置单元。

您可以通过构建你尝试导入的类型库的 32 位和 64 位版本中解决此错误，然后再注册这两个。  也可以使用本机 64 位编译器，因此你需要更改你**VC + + 目录**IDE 以指向 64 位编译器中的属性。

有关详细信息，请参阅

- [如何：在命令行上启用 64 位 Visual C++ 工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [如何：针对 64 位 x64 平台配置 Visual C++ 项目](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)