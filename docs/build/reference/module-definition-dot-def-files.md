---
title: 模块定义 (.Def) 文件
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321216"
---
# <a name="module-definition-def-files"></a>模块定义 (.Def) 文件

模块定义 (.def) 文件提供链接器提供有关导出、 属性和要链接的程序有关的其他信息。 .Def 文件生成 DLL 时最有用。 由于没有[MSVC 链接器选项](linker-options.md)，可以使用而不是模块定义语句.def 文件通常是不必要。 此外可以使用[__declspec （dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md)作为一种方法来指定导出的函数。

可以在链接器阶段调用.def 文件[/DEF （指定模块定义文件）](def-specify-module-definition-file.md)链接器选项。

如果要构建具有没有导出的.exe 文件，使用.def 文件将使输出文件更大和较慢加载速度。

有关示例，请参阅[DLL 使用 DEF 文件从导出](../exporting-from-a-dll-using-def-files.md)。

请参阅以下各节，有关详细信息：

- [模块定义语句的规则](rules-for-module-definition-statements.md)

- [EXPORTS](exports.md)

- [HEAPSIZE](heapsize.md)

- [LIBRARY](library.md)

- [NAME](name-c-cpp.md)

- [部分](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [VERSION](version-c-cpp.md)

- [保留的字](reserved-words.md)

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)<br/>
[MSVC 链接器选项](linker-options.md)
