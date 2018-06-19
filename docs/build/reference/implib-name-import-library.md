---
title: -IMPLIB （命名导入库） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edc0fcb1b216319d6f6c9924cb92a165b3196b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375267"
---
# <a name="implib-name-import-library"></a>/IMPLIB（命名导入库）
  
> /IMPLIB:*filename*  
  
## <a name="parameters"></a>参数  
  
*filename*  
导入库用户指定的名称。 它将替换默认名称。  
  
## <a name="remarks"></a>备注  
  
/IMPLIB 选项优先于 LINK 将创建它生成包含导出的程序时的导入库的默认名称。 默认名称构成的主输出文件和扩展名的基名称。 lib。 如果指定一个或多个以下，程序将包含导出：  
  
-   [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)的源代码中的关键字  
  
-   [导出](../../build/reference/exports.md)在.def 文件语句  
  
-   [/导出](../../build/reference/export-exports-a-function.md)LINK 命令中的规范  
  
 未能创建导入库时，链接将忽略 /IMPLIB。 如果未指定导出，链接将不创建导入库。 如果在生成中使用一个导出文件，则链接将假定导入库已存在，并且不会创建一个。 有关导入库和导出文件的信息，请参阅[LIB 引用](../../build/reference/lib-reference.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**导入库**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)