---
title: -MIDL （指定 MIDL 命令行选项） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3f20fddd657d1e5e57caf65ecc8e2c52afbf12
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42571651"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL（指定 MIDL 命令行选项）
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `file`  
 包含文件的名称[MIDL 命令行选项](http://msdn.microsoft.com/library/windows/desktop/aa366839)。  
  
## <a name="remarks"></a>备注  
 必须给定的 IDL 文件转换为 TLB 文件的所有选项`file`;不能链接器的命令行上指定 MIDL 命令行选项。 如果未指定 /MIDL，MIDL 编译器将调用使用 IDL 文件名称和任何其他选项。  
  
 该文件应包含每行一个 MIDL 命令行选项。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**嵌入的 IDL**属性页。  
  
4.  修改**MIDL 命令**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [/IDLOUT （命名 MIDL 输出文件）](../../build/reference/idlout-name-midl-output-files.md)   
 [/IGNOREIDL （不将属性处理到 MIDL）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/TLBOUT （名称。TLB 文件）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [生成特性化程序](../../windows/building-an-attributed-program.md)