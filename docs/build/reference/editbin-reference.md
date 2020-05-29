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
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328338"
---
# <a name="editbin-reference"></a>EDITBIN 参考

微软 COFF 二进制文件编辑器（EDITBIN）。EXE） 修改常见对象文件格式 （COFF） 二进制文件。 您可以使用 EDITBIN 修改对象文件、可执行文件和动态链接库 （DLL）。

> [!NOTE]
> 只能从可视化工作室命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

EDITBIN 不适用于使用[/GL](gl-whole-program-optimization.md)编译器选项生成的文件。 任何修改二进制文件与 /GL 将必须通过重新编译和链接来实现。

- [EDITBIN 命令行](editbin-command-line.md)

- [EDITBIN 选项](editbin-options.md)

## <a name="see-also"></a>另请参阅

[其他 MSVC 构建工具](c-cpp-build-tools.md)
