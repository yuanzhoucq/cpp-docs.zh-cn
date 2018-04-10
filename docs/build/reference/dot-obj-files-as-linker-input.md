---
title: .Obj 文件作为链接器输入 |Microsoft 文档
ms.custom: ''
ms.date: 12/29/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a2896822e97bdbb5ffdf8f869e67beadc1675b7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件

链接器工具 （链接。EXE) 接受在通用对象文件格式 (COFF) 的.obj 文件。

## <a name="remarks"></a>备注

Microsoft 提供了通用对象文件格式的完整说明。 有关详细信息，请参阅[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)。

## <a name="unicode-support"></a>Unicode 支持

Microsoft Visual c + + 编译器从 Visual Studio 2005 开始，支持 ISO/IEC C 和 c + + 标准定义的标识符中的 Unicode 字符。 以前版本的编译器支持在标识符中仅包含 ASCII 字符。 若要支持 Unicode 支持的函数、 类和静态对象的名称中，编译器和链接器，请使用 COFF 符号.obj 文件中的 Unicode utf-8 编码。 Utf-8 编码是与使用 Visual Studio 的早期版本的 ASCII 编码上级兼容。

有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123)组织。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)  
[链接器选项](../../build/reference/linker-options.md)  
[支持 Unicode](../../text/support-for-unicode.md)  
[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode 标准](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)  
