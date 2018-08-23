---
title: -TLBOUT （名称。TLB 文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc4103c387fe7a3dae68b642c10e326b361c54a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376847"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT（命名 .TLB 文件）
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *path*  
 应在其中创建.tlb 文件绝对或相对路径规范。  
  
 *filename*  
 指定 MIDL 编译器所创建的.tlb 文件的名称。 假定没有文件扩展名;指定*filename*.tlb 如果您希望具有.tlb 扩展名。  
  
## <a name="remarks"></a>备注  
 /TLBOUT 选项指定的名称和扩展名的.tlb 文件。  
  
 当链接包含的项目时，Visual c + + 链接器将调用 MIDL 编译器[模块](../../windows/module-cpp.md)属性。  
  
 如果未指定 /TLBOUT，.tlb 文件将获取其名称从[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*。 如果未指定 /IDLOUT，则将 vc70.tlb 调用.tlb 文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**嵌入 IDL**属性页。  
  
4.  修改**类型库**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [/IGNOREIDL （不特性处理到 MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL （指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [生成特性化程序](../../windows/building-an-attributed-program.md)