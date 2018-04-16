---
title: "-Zp （结构成员对齐） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d387e0ab020e96afb3e2975b5c8686b668cbc10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zp-struct-member-alignment"></a>/Zp（结构成员对齐）
控制结构的成员如何打包到内存并指定模块中的所有结构相同的封装。  
  
## <a name="syntax"></a>语法  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## <a name="remarks"></a>备注  
 指定此选项，第一个之后的每个结构成员会存储在成员类型的大小上或`n`-字节边界 (其中`n`是 1、 2、 4、 8 或 16)，两者中较小。  
  
 下表中列出了该可用值。  
  
 1  
 1 字节边界上的包结构。 与相同**/Zp**。  
  
 2  
 在 2 字节边界上的包结构。  
  
 4  
 在 4 字节边界上的包结构。  
  
 8  
 在 8 字节边界 （默认值） 上的包结构。  
  
 16  
 在 16 字节边界上的包结构。  
  
 除非有特定的对齐要求，不应使用此选项。  
  
 你还可以使用[包](../../preprocessor/pack.md)控制结构封装。 有关对齐的详细信息，请参阅：  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [__alignof 运算符](../../cpp/alignof-operator.md)  
  
-   [__unaligned](../../cpp/unaligned.md)  
  
-   [结构对齐示例](../../build/examples-of-structure-alignment.md)(特定于 x64)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**代码生成**属性页。  
  
4.  修改**结构成员对齐**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)