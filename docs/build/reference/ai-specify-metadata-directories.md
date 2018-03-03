---
title: "-AI （指定元数据目录） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs:
- C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e2f6cb90cd86dfc572c23ef6fd0e5661b339774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ai-specify-metadata-directories"></a>/AI（指定元数据目录）
指定在解析传递给 `#using` 指令的文件引用时编译器将搜索的目录。  
  
## <a name="syntax"></a>语法  
  
```  
/AIdirectory  
```  
  
## <a name="arguments"></a>自变量  
 `directory`  
 编译器要搜索的目录或路径。  
  
## <a name="remarks"></a>备注  
 只能将一个目录可以传递给**/AI**调用。 指定一个**/AI**每个要编译器搜索的路径选项。 例如，若要将 C:\Project\Meta 和 C:\Common\Meta 添加到的编译器搜索路径`#using`指令，添加`/AI"C:\Project\Meta" /AI"C:\Common\Meta"`到编译器命令行添加到每个目录或**其他 #using 目录**Visual Studio 中的属性。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在导航窗格中，选择**配置属性**， **C/c + +**，**常规**。  
  
3.  修改**其他 #using 目录**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [#using 指令](../../preprocessor/hash-using-directive-cpp.md)