---
title: "映射 （生成映射文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f01daff11d41263766b66ed335c60d4bf83ced45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="map-generate-mapfile"></a>/MAP（生成映射文件）
```  
/MAP[:filename]  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 用户指定映射文件的名称。 它将替换默认名称。  
  
## <a name="remarks"></a>备注  
 /MAP 选项通知链接器来创建映射文件。  
  
 默认情况下，链接器使用的基名称的程序和扩展.map 命名映射文件。 可选*filename*允许你重写映射文件的默认名称。  
  
 映射文件是文本文件，其中包含有关正被链接的程序的以下信息：  
  
-   模块名称，即该文件的基名称  
  
-   （不是从文件系统中） 在程序文件头中时间戳  
  
-   在程序中，包括每个组的起始地址的组的列表 (作为*部分*:*偏移量*)，长度、 组名称和类  
  
-   公共符号，包括每个地址的列表 (作为*部分*:*偏移量*)，符号名称、 平面地址和.obj 文件中定义了该符号  
  
-   入口点 (作为*部分*:*偏移量*)  
  
 [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)选项指定要包括映射文件中的其他信息。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**调试**属性页。  
  
4.  修改**生成映射文件**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)