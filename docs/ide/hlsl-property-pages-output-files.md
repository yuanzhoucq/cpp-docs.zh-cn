---
title: "HLSL 属性页： 输出文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs: C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04f6ad8889c9a713b3b64284b329c21d5a2cd49e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 属性页：输出文件
若要配置 HLSL 编译器 (fxc.exe) 的以下属性，使用其**输出文件**属性。 有关如何访问**输出文件**HLSL 文件夹中的属性页上看到[使用项目属性](../ide/working-with-project-properties.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **标头变量名称**  
 指定用于编码 HLSL 对象代码的数组的名称。 数组 HLSL 编译器包含是输出的头文件中。 标头文件的名称由指定**头文件的名称**属性。  
  
 此属性对应于**/Vn [名称]**命令行自变量。  
  
 **头文件的名称**  
 指定由 HLSL 编译器输出的标头文件的名称。 标头包含编码为一个数组的 HLSL 对象代码。 数组的名称由指定**标头变量名称**属性。  
  
 此属性对应于**/Fh [名称]**命令行自变量。  
  
 **对象文件名称**  
 指定由 HLSL 编译器输出的对象文件的名称。 默认情况下，值是**$(OutDir) %（文件名）.cso**。  
  
 此属性对应于**/Fo [名称]**命令行自变量。  
  
 **汇编程序输出**  
 **仅限程序集的列表 (/ Fc)**输出只是程序集语言语句。 **程序集代码和十六进制 (/ Fx)**输出程序集语言语句和相应的操作代码以十六进制表示。 默认情况下，没有列出是输出。  
  
 **汇编程序输出文件**  
 指定由 HLSL 编译器输出的程序集列表文件的名称。  
  
 此属性对应于**/Fc [名称]**和**/Fx [名称]**命令行自变量。  
  
## <a name="see-also"></a>请参阅  
 [HLSL 属性页](../ide/hlsl-property-pages.md)   
 [HLSL 属性页： 常规](../ide/hlsl-property-pages-general.md)   
 [HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)