---
title: 其他 MSVC 生成工具
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177293"
---
# <a name="additional-msvc-build-tools"></a>其他 MSVC 生成工具

Visual Studio 提供了以下命令行实用程序, 用于查看或操作生成输出:

- [LIB。EXE](lib-reference.md)用于创建和管理通用对象文件格式 (COFF) 对象文件的库。 它还可用于创建导出文件和导入库, 以便引用导出的定义。

- [EDITBIN。EXE](editbin-reference.md)用于修改 COFF 二进制文件。

- [DUMPBIN。EXE](dumpbin-reference.md)显示有关 COFF 二进制文件的信息 (如符号表)。

- [NMAKE](nmake-reference.md)读取和执行生成的。

- [ERRLOOK](value-edit-control.md), 错误查找实用工具根据输入的值检索系统错误消息或模块错误消息。

- [XDCMake](xdcmake-reference.md)。 用于处理源代码文件的工具, 其中包含用 XML 标记标记的文档注释。

- [BSCMAKE。EXE](bscmake-reference.md) (提供仅用于向后兼容性) 生成浏览信息文件 (.bsc), 该文件包含有关程序中的符号 (类、函数、数据、宏和类型) 的信息。 可在开发环境中的 "浏览" 窗口中查看此信息。 (.Bsc 文件也可以在开发环境中生成。)

Windows SDK 还包含若干生成工具, 包括[RC。EXE](/windows/win32/menurc/resource-compiler), C++编译器会调用它来编译本机 Windows 资源, 如对话框、属性页、位图、字符串表等。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)<br/>
[修饰名](decorated-names.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 链接器选项](linker-options.md)
