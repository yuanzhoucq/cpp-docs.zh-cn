---
title: "/Zf （更快地 PDB 生成） |Microsoft 文档"
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7012777643f993c552f79b58a02d4806c0ce4caa
ms.sourcegitcommit: c770a343def04ae77522708387c3f7c470e49969
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="zf-faster-pdb-generation"></a>/Zf （更快地 PDB 生成）

启用通过最小化对 mspdbsrv.exe 的 RPC 调用中并行生成更快的 PDB 生成。

## <a name="syntax"></a>语法

> **/Zf**

## <a name="remarks"></a>备注

**/Zf**选项使编译器支持更快地生成 PDB 文件时使用[/MP （使用多个进程生成）](mp-build-with-multiple-processes.md)选项，或当生成系统 (例如， [MSBuild](/visualstudio/msbuild/msbuild-reference)或[CMake](../../ide/cmake-tools-for-visual-cpp.md)) 可能运行多个 cl.exe 编译器进程在同一时间。 此选项会导致编译器前端延迟生成的类型索引的 PDB 文件中每个类型记录直至结束编译，然后对 mspdbsrv.exe，而不是进行每个记录的 RPC 请求的单个 RPC 调用中的所有请求它们。 通过减少中多个 cl.exe 编译器进程同时运行的环境的 mspdbsrv.exe 过程的 RPC 负载，这可以显著提高生成吞吐量。

因为**/Zf**选项仅适用于 PDB 的生成，它需要[/Zi](z7-zi-zi-debug-information-format.md)或[/ZI](z7-zi-zi-debug-information-format.md)选项。

**/Zf**选项 Visual Studio 2017 15.1，版中开始提供，并默认处于关闭状态。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含**/Zf** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[按字母顺序列出的编译器选项](compiler-options-listed-alphabetically.md)  
[/MP（使用多个进程生成）](mp-build-with-multiple-processes.md)  
