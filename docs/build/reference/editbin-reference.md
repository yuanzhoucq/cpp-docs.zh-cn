---
title: EDITBIN 参考
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: c2c0ee66ed1811755edc33b24737e057554fd01f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542894"
---
# <a name="editbin-reference"></a>EDITBIN 参考

Microsoft COFF 二进制文件编辑器 (EDITBIN。EXE) 修改通用对象文件格式 (COFF) 的二进制文件。 可以使用 EDITBIN 来修改对象文件、 可执行文件或动态链接库 (DLL)。

> [!NOTE]
>  可以仅从 Visual Studio 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

EDITBIN 不是可用于与生成文件[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。 对使用 /GL 生成的二进制文件进行任何修改将需要通过重新编译和链接。

- [EDITBIN 命令行](../../build/reference/editbin-command-line.md)

- [EDITBIN 选项](../../build/reference/editbin-options.md)

## <a name="see-also"></a>请参阅

[C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)