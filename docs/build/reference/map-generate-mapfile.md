---
title: -映射 （生成映射文件） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c39134f45b1a044a76139d33aa9e761a0f14c8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725577"
---
# <a name="map-generate-mapfile"></a>/MAP（生成映射文件）

```
/MAP[:filename]
```

## <a name="arguments"></a>自变量

*filename*<br/>
用户指定映射文件的名称。 它将替换默认名称。

## <a name="remarks"></a>备注

/MAP 选项告知链接器创建映射文件。

默认情况下，链接器的基名称的程序和扩展.map 命名映射文件。 可选*文件名*允许你重写映射文件的默认名称。

映射文件是文本文件，其中包含要链接的程序有关的以下信息：

- 模块名称，即该文件的基名称

- 从程序文件标头 （不是从文件系统） 时间戳

- 在程序中，包括每个组的起始地址的组的列表 (作为*一节*:*偏移量*)，长度、 组名称和类

- 公共符号，与每个地址的列表 (作为*一节*:*偏移量*)，符号名称、 平面地址和.obj 文件中定义了符号

- 入口点 (作为*一节*:*偏移量*)

[/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)选项指定要包含在映射文件中的其他信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**调试**属性页。

1. 修改**生成映射文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)