---
title: -INCLUDE （强制符号引用） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfe65344e41b98841c3a4e7bca72b762197510b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375644"
---
# <a name="include-force-symbol-references"></a>/INCLUDE（强制符号引用）
```  
/INCLUDE:symbol  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `symbol`  
 指定要添加到符号表的符号。  
  
## <a name="remarks"></a>备注  
 /INCLUDE 选项通知链接器将指定的符号添加到符号表。  
  
 若要指定多个符号，请键入逗号 （，）、 分号 （;） 或符号名之间留一个空格。 在命令行中，指定 /INCLUDE:`symbol`一次针对每个符号。  
  
 链接器解析`symbol`通过添加包含到程序的符号定义的对象。 此功能可用于包括否则不会对程序链接的库对象。  
  
 使用此选项指定符号重写由该符号的移除[/opt: ref](../../build/reference/opt-optimizations.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**输入**属性页。  
  
4.  修改**强制符号引用**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)