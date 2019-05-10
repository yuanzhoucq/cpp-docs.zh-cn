---
title: 多线程编程的包含文件
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: 79b5c56eecfaf28743eec4ba6b4cee56156d6e2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212878"
---
# <a name="include-files-for-multithreading"></a>多线程编程的包含文件

标准包含文件将 C 运行时库函数声明为库中实现它们。 如果您使用[完全优化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 调用约定](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 选项，编译器会假定应该使用的寄存器调用约定来调用的所有函数。 运行时库函数使用 C 调用约定，编译和标准包含文件中的声明指示编译器生成正确的外部引用，这些函数。

## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)
