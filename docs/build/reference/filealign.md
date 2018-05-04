---
title: / FILEALIGN （文件中的对齐部分） |Microsoft 文档
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a737801663a2c7c1e896166291a1635fbbe6c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="filealign-align-sections-in-files"></a>/ FILEALIGN （文件中的对齐部分）

**/FILEALIGN**链接器选项，您指定为指定大小的倍数，写入到输出文件的各节的对齐方式。

## <a name="syntax"></a>语法

> __/ FILEALIGN:__*大小*

### <a name="parameters"></a>参数

*size*  
节对齐的大小以字节为单位，它必须是 2 的幂。

## <a name="remarks"></a>备注

**/FILEALIGN**选项导致链接器对齐的倍数的边界上的输出文件中的每一部分*大小*值。 默认情况下，链接器不使用固定的对齐方式大小。

**/FILEALIGN**选项可用来使磁盘利用率更加有效，或将页面从磁盘加载速度更快。 较小的部分大小可能可用于运行小型设备上或者保留下载较小的应用程序。 节对齐在磁盘上的不会影响在内存中的对齐方式。

使用 [DUMPBIN](dumpbin-reference.md) 可查看有关输出文件中各节的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**命令行**中的属性页**链接器**文件夹。

1. 键入选项名 **/FILEALIGN:** 和的大小以**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)   
[链接器选项](../../build/reference/linker-options.md)