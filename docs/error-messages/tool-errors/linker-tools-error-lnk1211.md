---
title: 链接器工具错误 LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: 7c918cacb87460c2aad30285b750d9b170425534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242664"
---
# <a name="linker-tools-error-lnk1211"></a>链接器工具错误 LNK1211

> 找不到; 预编译的类型信息'*文件名*未链接或覆盖

*文件名*通过使用编译的对象文件[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 LINK 命令中未指定或已被覆盖。

如果要创建的调试库使用预编译标头，如果您指定 **/Yc**并[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)、 VisualC++生成包含调试信息的预编译的对象文件。 出错仅存储时的预编译的对象文件在库中，使用库来生成可执行文件的映像，并且引用的对象文件具有对预编译的对象文件定义的任何的函数可传递的引用。

有两种方法，若要解决这种情况：

- 指定[/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)编译器选项将调试信息从的预编译标头添加到每个对象模块。 此方法不太可取，因为它通常会生成大型对象模块，可提高链接应用程序所需的时间。

- 指定[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)并创建不包含任何函数定义的预编译标头文件时将传递任何任意字符串的名称。 这会指示编译器在预编译的对象文件中创建一个符号，并发出对每个对象文件使用预编译的对象文件与相关联的预编译标头文件中该符号的引用。

编译的模块时 **/Yc**并 **/Yl**，则编译器会创建一个符号类似于`__@@_PchSym_@00@...@symbol_name`，其中的省略号 （...） 表示是编译器生成的字符串，并将其存储在对象模块。 任何使用此预编译标头进行编译的源文件是指导致链接器包括对象模块和其库中的调试信息的指定符号。
