---
title: "-/doc （处理文档注释） （C/c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8737c0e33d33fe062d9a07f18d9005e58463f5b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="doc-process-documentation-comments-cc"></a>/doc（处理文档注释）(C/C++)
在源代码文件中并创建具有文档注释每个源代码文件的.xdc 文件可让编译器处理文档注释。  
  
## <a name="syntax"></a>语法  
  
```  
/doc[name]  
```  
  
## <a name="arguments"></a>自变量  
 `name`  
 编译器将创建到.xdc 文件的名称。 仅当在编译中传递一个.cpp 文件时才有效。  
  
## <a name="remarks"></a>备注  
 .Xdc 文件处理到具有 xdcmake.exe 的.xml 文件。 有关详细信息，请参阅[XDCMake 参考](../../ide/xdcmake-reference.md)。  
  
 可以将文档注释添加到源代码文件。 有关详细信息，请参阅[建议的文档注释标记](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
 若要使用 IntelliSense 生成的.xml 文件，请与你想要支持，并将.xml 文件的程序集相同的程序集相同的目录中的.xml 文件的文件名称。 当 Visual Studio 项目中引用的程序集时，还找到.xml 文件。 有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)和[提供 XML 代码注释](/visualstudio/ide/supplying-xml-code-comments)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**C/c + +**节点。  
  
4.  选择**输出文件**属性页。  
  
5.  修改**生成 XML 文档文件**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)