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
ms.openlocfilehash: c55c3181c2ddfabddce882a473e56d952a7e5d81
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816394"
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件

链接器工具 （链接。EXE) 接受是通用对象文件格式 (COFF) 中的.obj 文件。

## <a name="remarks"></a>备注

Microsoft 提供了通用对象文件格式的完整说明。 有关详细信息，请参阅[PE 格式](/windows/desktop/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支持

从 Visual Studio 2005 开始，Microsoft MSVC 编译器支持在标识符 ISO/IEC C 和 c + + 标准定义的 Unicode 字符。 以前版本的编译器支持在标识符中仅包含 ASCII 字符。 若要支持 Unicode 的函数、 类和静态变量的名称中，编译器和链接器，请使用.obj 文件中的 COFF 符号的 Unicode utf-8 编码。 Utf-8 编码是与使用 Visual Studio 的早期版本的 ASCII 编码向上兼容。

有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[Unicode](http://www.unicode.org/)组织。

## <a name="see-also"></a>请参阅

[LINK 输入文件](link-input-files.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[支持 Unicode](../../text/support-for-unicode.md)<br/>
[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 标准](http://www.unicode.org/)<br/>
[PE 格式](/windows/desktop/Debug/pe-format)
