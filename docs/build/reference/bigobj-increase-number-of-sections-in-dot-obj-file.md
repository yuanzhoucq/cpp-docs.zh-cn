---
title: "-bigobj （增加数中的部分。Obj 文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /bigobj
dev_langs: C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384ec0de9e5cb1b3172b980bf7f412abe759ff91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj（增加 .Obj 文件中的节数）
**/bigobj 进行编译**增加的对象文件可以包含的节的数目。  
  
## <a name="syntax"></a>语法  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，对象文件可以保存最多 65536 (2 ^16) 可寻址节。 无论指定哪个目标平台都是如此。 **/bigobj 进行编译**增加到 4294967296 该地址容量 (2 ^32)。  
  
 大多数模块将永远不会生成一个包含节数超过 65536 的.obj 文件。 但是，计算机生成的代码，或者使大量使用模板库的代码可能需要.obj 文件，其中可以保存多个部分。 **/bigobj 进行编译**因为计算机生成的 XAML 代码包含大量标头，默认情况下，在 Windows 应用商店项目启用。 如果对 Windows 应用商店应用项目禁用此选项，则可能会遇到编译器错误 C1128。  
  
 提供使用 Visual c + + 2005年之前的链接不能读取与生成的.obj 文件**/bigobj 进行编译**。  
  
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