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
ms.openlocfilehash: 304c9861b85be1925e48d47c6006fcbcdd41dc22
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791592"
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件

链接器工具（链接）。EXE）接受通用对象文件格式（COFF）的 .obj 文件。

## <a name="remarks"></a>备注

Microsoft 提供了通用对象文件格式的完整说明。 有关详细信息，请参阅[PE 格式](/windows/win32/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支持

从 Visual Studio 2005 开始，Microsoft MSVC 编译器支持 ISO/IEC C 和C++标准定义的标识符中的 Unicode 字符。 以前版本的编译器仅支持标识符中的 ASCII 字符。 为了支持函数、类和静态函数名称中的 Unicode，编译器和链接器使用 .obj 文件中 COFF 符号的 Unicode UTF-8 编码。 UTF-8 编码与 Visual Studio 早期版本使用的 ASCII 编码 upwardly 兼容。

有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[unicode](https://home.unicode.org/)组织。

## <a name="see-also"></a>另请参阅

[LINK 输入文件](link-input-files.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[支持 Unicode](../../text/support-for-unicode.md)<br/>
[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 标准](https://home.unicode.org/)<br/>
[PE 格式](/windows/win32/Debug/pe-format)
