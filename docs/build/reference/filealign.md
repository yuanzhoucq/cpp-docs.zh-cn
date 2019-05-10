---
title: /FILEALIGN （对齐文件中的部分）
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271146"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN （对齐文件中的部分）

**/FILEALIGN**链接器选项可以指定部分写入到输出文件的指定大小的倍数的对齐方式。

## <a name="syntax"></a>语法

> __/FILEALIGN:__*大小*

### <a name="parameters"></a>参数

*size*<br/>
节对齐的大小以字节为单位，它必须是 2 的幂。

## <a name="remarks"></a>备注

**/FILEALIGN**选项将使链接器将对齐的倍数的边界上的输出文件中的每一部分*大小*值。 默认情况下，链接器不使用固定的对齐大小。

**/FILEALIGN**选项可用于提高磁盘利用率的效率，或将页面从磁盘加载速度更快。 较小的部分可能可用于运行在较小的设备，或者保留下载较小的应用程序。 节对齐磁盘上的不会影响在内存中的对齐方式。

使用 [DUMPBIN](dumpbin-reference.md) 可查看有关输出文件中各节的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**命令行**中的属性页**链接器**文件夹。

1. 键入选项名 **/FILEALIGN:** 以及中的大小**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
