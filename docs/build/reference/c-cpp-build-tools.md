---
title: 其他 MSVC 生成工具
ms.date: 05/06/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 59c9cb4527de878b06cbb6a7b3abe921e9a60107
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220219"
---
# <a name="additional-msvc-build-tools"></a>其他 MSVC 生成工具

Visual Studio 提供了以下命令行实用程序用于查看或操作生成输出：


- [LIB。EXE](lib-reference.md)用于创建和管理通用对象文件格式 (COFF) 对象文件的库。 它还可以用来创建导出文件和导入库，以便引用导出的定义。

- [EDITBIN。EXE](editbin-reference.md)用于修改 COFF 二进制文件。

- [DUMPBIN。EXE](dumpbin-reference.md)显示 COFF 二进制文件 （例如，符号表） 上的信息。

- [NMAKE](nmake-reference.md)读取并执行生成文件。

- [ERRLOOK](value-edit-control.md)，错误查找实用工具检索系统错误消息或模块错误消息根据输入的值。

- [XDCMake](xdcmake-reference.md)。 处理包含文档注释的源代码文件 toolfor 标有 XML 标记中。

- [BSCMAKE。EXE](bscmake-reference.md) （只是为了向后兼容提供） 生成浏览信息文件 (.bsc) 包含在程序中的符号 （类、 函数、 数据、 宏和类型） 的信息。 在开发环境内的浏览窗口中查看此信息。 （.bsc 文件也可以生成在开发环境中。）

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)<br/>
[修饰名](decorated-names.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 链接器选项](linker-options.md)
