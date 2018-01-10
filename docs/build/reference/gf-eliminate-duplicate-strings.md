---
title: "-GF （消除重复的字符串） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
dev_langs: C++
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d69e892fb9487b66da4dfa2a801bab302e962af7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF（消除重复的字符串）
使编译器能够在执行过程中的程序映像和内存中创建的相同字符串的单个副本。 这是一种优化方式调用*字符串池*，它可以创建较小的程序。  
  
## <a name="syntax"></a>语法  
  
```  
/GF  
```  
  
## <a name="remarks"></a>备注  
 如果你使用**/GF**，操作系统不交换的内存的字符串部分和可以读回从图像文件的字符串。  
  
 **/GF**池以只读方式的字符串。 如果你尝试在下修改字符串**/GF**，发生应用程序错误。  
  
 字符串池允许用作多个缓冲区的多个指针是指向单个缓冲区的多个指针。 在下面的代码中，`s`和`t`使用相同的字符串初始化。 字符串池使它们指向相同的内存：  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)选项，用于编辑并继续，将自动设置**/GF**选项。  
  
> [!NOTE]
>  **/GF**编译器选项会创建每个唯一字符串的可寻址节。 并且默认情况下，对象文件可以包含最多 65536 可寻址节。 如果你的程序包含多个 65,536 字符串，使用[/bigobj 进行编译](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)编译器选项来创建多个部分。  
  
 **/GF**有效时[/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或**/O2**使用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**代码生成**属性页。  
  
4.  修改**启用字符串池**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)