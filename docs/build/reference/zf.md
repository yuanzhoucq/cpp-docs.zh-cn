---
title: /Zf （更快的 PDB 生成）
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: bed37a189e3eb1eb7b55dbdee1f81f360eafa721
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814041"
---
# <a name="zf-faster-pdb-generation"></a>/Zf （更快的 PDB 生成）

通过在并行生成 PDB 更快生成最大程度减少对 mspdbsrv.exe 的 RPC 调用。

## <a name="syntax"></a>语法

> **/Zf**

## <a name="remarks"></a>备注

**/Zf**选项更快地生成 PDB 文件的编译器支持使用时启用[/MP （使用多个进程生成）](mp-build-with-multiple-processes.md)选项，或当生成系统 (例如， [MSBuild](/visualstudio/msbuild/msbuild-reference)或[CMake](../cmake-projects-in-visual-studio.md)) 可能会运行多个 cl.exe 编译器进程在同一时间。 此选项导致编译器前端延迟生成类型索引的 PDB 文件中每个类型记录的结束前的编译，则对 mspdbsrv.exe，而不是使每个记录的 RPC 请求的单个 RPC 调用中的所有请求。 这可以大大减少多个 cl.exe 编译器进程同时运行的环境中的 mspdbsrv.exe 过程 RPC 负载，从而改进生成吞吐量。

因为 **/Zf**选项仅适用于 PDB 生成，它需要[/Zi](z7-zi-zi-debug-information-format.md)或[/ZI](z7-zi-zi-debug-information-format.md)选项。

**/Zf**选项是在 Visual Studio 2017 版本 15.1，开始提供，它默认处于关闭状态。 开始在 Visual Studio 2017 版本 15.7 预览版 3 中，此选项默认为打开时 **/Zi**或 **/ZI**选项处于启用状态。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zf** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[按字母顺序列出的编译器选项](compiler-options-listed-alphabetically.md)<br/>
[/MP（使用多个进程生成）](mp-build-with-multiple-processes.md)<br/>
