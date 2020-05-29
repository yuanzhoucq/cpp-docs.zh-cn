---
title: 编译器控制的 LINK 选项
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440105"
---
# <a name="compiler-controlled-link-options"></a>编译器控制的 LINK 选项

除非您指定/c 选项，否则 CL 编译器会自动调用 LINK。 CL 通过命令行选项和参数提供对链接器的一些控制。 下表汇总了 CL 中影响链接的功能。

|CL 规范|影响链接的 CL 操作|
|----------------------|---------------------------------|
|除 .c、. .cxx、.cpp 或 .def 之外的任何文件扩展名|将文件名作为输入传递给 LINK|
|*文件名*.def|传递/DEF：*文件名*.def|
|/F*编号*|Pass/STACK：*number*|
|/Fd*filename*|传递/PDB：*filename*|
|/Fe*filename*|传递/OUT：*filename*|
|/Fm*filename*|传递/MAP：*filename*|
|/Gy|创建打包函数（Comdat）;启用函数级链接|
|/LD|传递/DLL|
|/LDd|传递/DLL|
|/link|传递要链接的命令行的其余部分|
|/MD 或/MT|在 .obj 文件中放置默认库名称|
|/MDd 或/MTd|将默认的库名称放在 .obj 文件中。 定义符号 **_DEBUG**|
|/nologo|传递/NOLOGO|
|/Zd|传递/DEBUG|
|/Zi 或/Z7|传递/DEBUG|
|/Zl|省略 .obj 文件中的默认库名称|

有关详细信息，请参阅[MSVC 编译器选项](compiler-options.md)。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
