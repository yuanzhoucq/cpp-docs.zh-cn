---
title: -V （版本号） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3daf62c818b454a5477de04a27c4b4f308c271d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="v-version-number"></a>/V（版本号）
已否决。 .Obj 文件中嵌入的文本字符串。  
  
## <a name="syntax"></a>语法  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>自变量  
 `string`  
 一个字符串，指定要在.obj 文件中嵌入的版本号或版权声明。  
  
## <a name="remarks"></a>备注  
 字符串标签具有版本号或版权声明的.obj 文件中。 如果它们是字符串的一部分，任何空格或制表符字符必须括在双引号 （"）。 反斜杠 (\\) 如果它们是字符串的一个部分都必须位于任何两个双引号之前。 之间留一个空格 **/V**和`string`是可选的。  
  
 你还可以使用[注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)与编译器注释类型参数，以将编译器的名称和版本数放在.obj 文件。  
  
 **/V**选项在 Visual Studio 2005; 从开始已弃用 **/V**是主要用于支持生成虚拟设备驱动程序 (VxDs) 和 Visual c + + 工具集不再支持生成 VxDs。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
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