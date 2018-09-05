---
title: .Obj 文件作为链接器输入 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd1fbd635b1d3d3a5f9963edaa9f22e22472dad1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691746"
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件

链接器工具 （链接。EXE) 接受是通用对象文件格式 (COFF) 中的.obj 文件。

## <a name="remarks"></a>备注

Microsoft 提供了通用对象文件格式的完整说明。 有关详细信息，请参阅[PE 格式](/windows/desktop/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支持

从 Visual Studio 2005 开始，Microsoft Visual c + + 编译器支持在标识符 ISO/IEC C 和 c + + 标准定义的 Unicode 字符。 以前版本的编译器支持在标识符中仅包含 ASCII 字符。 若要支持 Unicode 的函数、 类和静态变量的名称中，编译器和链接器，请使用.obj 文件中的 COFF 符号的 Unicode utf-8 编码。 Utf-8 编码是与使用 Visual Studio 的早期版本的 ASCII 编码向上兼容。

有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[Unicode](http://www.unicode.org/)组织。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)  
[链接器选项](../../build/reference/linker-options.md)  
[支持 Unicode](../../text/support-for-unicode.md)  
[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode 标准](http://www.unicode.org/)  
[PE 格式](/windows/desktop/Debug/pe-format)  
