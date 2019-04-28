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
ms.openlocfilehash: 45c2967a55e85ae31bb77bb2e8d50415eafbea46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293025"
---
# <a name="editbin-reference"></a>EDITBIN 参考

Microsoft COFF 二进制文件编辑器 (EDITBIN。EXE) 修改通用对象文件格式 (COFF) 的二进制文件。 可以使用 EDITBIN 来修改对象文件、 可执行文件或动态链接库 (DLL)。

> [!NOTE]
>  可以仅从 Visual Studio 命令提示符启动此工具。 无法从系统命令提示符或文件资源管理器中启动它。

EDITBIN 不是可用于与生成文件[/GL](gl-whole-program-optimization.md)编译器选项。 对使用 /GL 生成的二进制文件进行任何修改将需要通过重新编译和链接。

- [EDITBIN 命令行](editbin-command-line.md)

- [EDITBIN 选项](editbin-options.md)

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)
