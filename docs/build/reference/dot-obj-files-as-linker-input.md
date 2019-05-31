---
title: 用作链接器输入的 .Obj 文件
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 36f41077fcba6b093865625d426b8009f6185e7b
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450575"
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件

链接器工具 （链接。EXE) 接受是通用对象文件格式 (COFF) 中的.obj 文件。

## <a name="remarks"></a>备注

Microsoft 提供了通用对象文件格式的完整说明。 有关详细信息，请参阅[PE 格式](/windows/desktop/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支持

从 Visual Studio 2005 开始，Microsoft MSVC 编译器支持 Unicode 字符在标识符中定义的 ISO/IEC C 和C++标准。 以前版本的编译器支持在标识符中仅包含 ASCII 字符。 若要支持 Unicode 的函数、 类和静态变量的名称中，编译器和链接器，请使用.obj 文件中的 COFF 符号的 Unicode utf-8 编码。 Utf-8 编码是与使用 Visual Studio 的早期版本的 ASCII 编码向上兼容。

有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[Unicode](https://www.unicode.org/)组织。

## <a name="see-also"></a>请参阅

[LINK 输入文件](link-input-files.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[支持 Unicode](../../text/support-for-unicode.md)<br/>
[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 标准](https://www.unicode.org/)<br/>
[PE 格式](/windows/desktop/Debug/pe-format)
