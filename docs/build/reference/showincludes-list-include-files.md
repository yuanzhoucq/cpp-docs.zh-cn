---
title: -showIncludes （列表包含文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb88ff6d8a314ebd5cb0390f2c920f5b1d04e3e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="showincludes-list-include-files"></a>/showIncludes（列出包含文件）
使编译器将输出包含文件的列表。 嵌套包括文件还可以显示 （文件从你包含的文件所包含的）。  
  
## <a name="syntax"></a>语法  
  
```  
/showIncludes  
```  
  
## <a name="remarks"></a>备注  
 当在编译期间遇到的包含文件时，则输出消息，例如：  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 嵌套包括由缩进，每个级别的嵌套，使用一个空格例如指示文件：  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 在这种情况下，`2.h`已包含在`1.h`，因此缩进。  
  
 **/ShowIncludes**选项发出到`stderr`，而不`stdout`。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**显示包括**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)