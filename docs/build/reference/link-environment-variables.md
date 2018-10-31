---
title: LINK 环境变量
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
ms.openlocfilehash: 3a398787530794f5a08d6cd122e55c305e265062
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434406"
---
# <a name="link-environment-variables"></a>LINK 环境变量

LINK 工具使用以下环境变量：

- 链接和\_链接\_，如果定义。 LINK 工具预置的选项和链接的环境变量中定义的自变量并追加选项和参数中定义\_链接\_之前处理的命令行自变量的环境变量。

- LIB（如已定义）。 LINK 工具搜索对象、 库或在命令行上或通过指定其他文件时使用 LIB 路径[/base](../../build/reference/base-base-address.md)选项。 它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。 LIB 变量可以包含一个或多个路径规范，用分号分隔。 一个路径必须指向 Visual C++ 安装的 \lib 子目录。

- PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。 （LINK 需要 CVTRES 链接 .res 文件。）PATH 必须指向 Visual C++ 安装的 \bin 子目录。

- TMP，用于链接 OMF 或.res 文件时指定目录。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>
[在命令行上生成 C/C++ 代码](../../build/building-on-the-command-line.md)<br/>
[为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
