---
title: "-Zs （只进行语法检查） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zs
dev_langs: C++
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44029bfb9b5753161319e565d9d25b732c635dfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zs-syntax-check-only"></a>/Zs（只进行语法检查）
告知编译器只检查语法的命令行上的源文件。  
  
## <a name="syntax"></a>语法  
  
```  
/Zs  
```  
  
## <a name="remarks"></a>备注  
 使用此选项时，不创建任何输出文件，并错误消息写入到标准输出。  
  
 **/Zs**选项提供查找和更正语法错误，然后编译和链接源文件的快速方法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)