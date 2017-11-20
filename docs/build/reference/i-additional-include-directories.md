---
title: "-I (附加包含目录) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs: C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91868a657e4b537c286378276701915c1e160a77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="i-additional-include-directories"></a>/I（附加包含目录）
将目录添加到用于搜索包含文件的目录的目录列表。  
  
## <a name="syntax"></a>语法  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>参数  
 `directory`  
 要添加到的目录列表的目录搜索包含文件。  
  
## <a name="remarks"></a>备注  
 若要添加多个目录，请多次使用此选项。 仅之前找到指定的包含文件搜索的目录。  
  
 忽略标准包括路径上使用此选项 ([/X （忽略标准包括路径）](../../build/reference/x-ignore-standard-include-paths.md)) 选项。  
  
 编译器将搜索目录按以下顺序：  
  
1.  包含的源文件的目录。  
  
2.  用指定的目录**/I**选项，CL 遇到它们的顺序。  
  
3.  中指定的目录**包括**环境变量。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**附加包含目录**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。  
  
## <a name="example"></a>示例  
 以下命令查找请求的 MAIN.c 按以下顺序包含文件： 包含 MAIN.c，然后在 \INCLUDE 目录中，然后在 \MY\INCLUDE 目录中，和最后的目录中分配给在包括的目录中的第一行环境变量。  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>另请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)