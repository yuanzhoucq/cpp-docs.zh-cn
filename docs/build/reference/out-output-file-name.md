---
title: -OUT （输出文件名） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fd9ec1b1631104355e076071370f627a36b4037
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376100"
---
# <a name="out-output-file-name"></a>/OUT（输出文件名）
```  
/OUT:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 输出文件的用户指定的名称。 它将替换默认名称。  
  
## <a name="remarks"></a>备注  
 /OUT 选项重写的默认名称和链接器将创建的程序位置。  
  
 默认情况下，链接器窗体使用指定的第一个.obj 文件和适当的扩展名 （.exe 或.dll） 的基名称的文件名称。  
  
 此选项.mapfile 或导入的库的默认基名称。 有关详细信息，请参阅[生成映射文件](../../build/reference/map-generate-mapfile.md)（/ 映射） 和[/IMPLIB](../../build/reference/implib-name-import-library.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**输出文件**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)