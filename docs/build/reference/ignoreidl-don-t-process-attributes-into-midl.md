---
title: -IGNOREIDL (Don&#39;到 MIDL t 进程特性) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14d32be32f019e55f8bad9cc01199d8dc6ae6301
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373447"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;到 MIDL t 过程属性)
```  
/IGNOREIDL  
```  
  
## <a name="remarks"></a>备注  
 /IGNOREIDL 选项指定的任何[IDL 特性](../../windows/idl-attributes.md)在源中的代码不应处理到.idl 文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**嵌入 IDL**属性页。  
  
4.  修改**忽略嵌入的 IDL**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [/IDLOUT （命名 MIDL 输出文件）](../../build/reference/idlout-name-midl-output-files.md)   
 [/TLBOUT （名称。TLB 文件）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [/MIDL （指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [生成特性化程序](../../windows/building-an-attributed-program.md)