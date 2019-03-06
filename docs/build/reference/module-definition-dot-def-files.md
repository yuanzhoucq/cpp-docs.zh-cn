---
title: 模块定义 (.Def) 文件
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 041894fa88527061d90399540bc29762bff66f81
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424530"
---
# <a name="module-definition-def-files"></a>模块定义 (.Def) 文件

模块定义 (.def) 文件提供链接器提供有关导出、 属性和要链接的程序有关的其他信息。 .Def 文件生成 DLL 时最有用。 由于没有[链接器选项](../../build/reference/linker-options.md)，可以使用而不是模块定义语句.def 文件通常是不必要。 此外可以使用[__declspec （dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md)作为一种方法来指定导出的函数。

可以在链接器阶段调用.def 文件[/DEF （指定模块定义文件）](../../build/reference/def-specify-module-definition-file.md)链接器选项。

如果要构建具有没有导出的.exe 文件，使用.def 文件将使输出文件更大和较慢加载速度。

有关示例，请参阅[DLL 使用 DEF 文件从导出](../../build/exporting-from-a-dll-using-def-files.md)。

请参阅以下各节，有关详细信息：

- [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTS](../../build/reference/exports.md)

- [HEAPSIZE](../../build/reference/heapsize.md)

- [LIBRARY](../../build/reference/library.md)

- [NAME](../../build/reference/name-c-cpp.md)

- [部分](../../build/reference/sections-c-cpp.md)

- [STACKSIZE](../../build/reference/stacksize.md)

- [STUB](../../build/reference/stub.md)

- [VERSION](../../build/reference/version-c-cpp.md)

- [保留的字](../../build/reference/reserved-words.md)

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
