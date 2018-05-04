---
title: -IDLOUT （命名 MIDL 输出文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7eeb7af3d19a57b6948f867df87b8d04d0397b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT（命名 MIDL 输出文件）
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>参数  
 *path*  
 绝对或相对路径规范。 通过指定的路径，你仅影响位置的.idl 文件;所有其他文件放置在项目目录中。  
  
 *filename*  
 指定 MIDL 编译器所创建的.idl 文件的名称。 假定没有文件扩展名;指定*filename*.idl 如果你想.idl 扩展。  
  
## <a name="remarks"></a>备注  
 /IDLOUT 选项指定的名称和.idl 文件扩展名。  
  
 当链接包含的项目时，Visual c + + 链接器将调用 MIDL 编译器[模块](../../windows/module-cpp.md)属性。  
  
 /IDLOUT 还指定与 MIDL 编译器关联的其他输出文件的文件名：  
  
-   *filename*.tlb  
  
-   *filename*_p.c  
  
-   *filename*_i.c  
  
-   *filename*.h  
  
 *filename*是传递给 /IDLOUT 参数。 如果[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md) .tlb 文件将从 /TLBOUT 获取其名称的指定*filename*。  
  
 如果你没有指定 /IDLOUT 和 /TLBOUT，链接器将创建 vc70.tlb、 vc70.idl、 vc70_p.c、 vc70_i.c 和 vc70.h。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**嵌入 IDL**属性页。  
  
4.  修改**合并的 IDL 基文件名**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [/IGNOREIDL （不特性处理到 MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL （指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [生成特性化程序](../../windows/building-an-attributed-program.md)