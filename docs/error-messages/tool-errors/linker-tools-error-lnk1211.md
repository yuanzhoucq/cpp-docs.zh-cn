---
title: "链接器工具错误 LNK1211 |Microsoft 文档"
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1211
dev_langs: C++
helpviewer_keywords: LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51150fb2a57f48f04cca97e5f16fe1a28ead2c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1211"></a>链接器工具错误 LNK1211

> 找不到; 的预编译的类型信息*filename*没有链接或覆盖

*Filename*对象文件中，使用编译的[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 LINK 命令中未指定，或者已被覆盖。

如果要创建调试库使用预编译标头和你指定**/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，Visual c + + 生成包含调试信息的预编译的对象文件。 仅当你将预编译的对象文件存储在库时，发生了错误，使用库来生成可执行文件的映像，，引用这些对象文件中包含到任何预编译的对象文件定义的函数没有可传递引用。

有两种方法要解决此情况：

- 指定[/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)编译器选项将调试信息从的预编译标头添加到每个对象模块。 此方法是不够理想，因为它通常会生成大型对象模块，可提高链接应用程序所需的时间。

- 指定[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) ，然后创建不包含任何函数定义的预编译标头文件时传递任何任意字符串的名称。 这指示编译器在预编译的对象文件中创建符号并发出对每个对象文件使用预编译的对象文件与相关联的预编译标头文件中该符号的引用。

编译的模块时**/Yc**和**/Yl**，编译器将创建一个符号类似于`__@@_PchSym_@00@...@symbol_name`，其中的省略号 （...） 表示是编译器生成的字符串，并将其存储在对象模块。 使用此预编译标头进行编译任何源文件引用指定的符号，这导致链接器包括对象模块和其库中的调试信息。
