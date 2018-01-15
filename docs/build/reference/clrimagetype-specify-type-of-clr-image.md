---
title: "-CLRIMAGETYPE （指定 CLR 映像的类型） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs: C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7d8edd6c9e62456e54ac6228f25d7f923a6813c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE（指定 CLR 映像的类型）
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>备注  
 链接器接受本机对象以及 MSIL 对象编译的使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，/clr: pure，或 /clr: safe。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。 同一版本中传递混合对象时，结果输出文件的可验证性级别默认等于输入模块的最低可验证性级别。 例如，将安全和纯模块同时传递给链接器时，输出文件将为纯文件。 如果传递本机映像和混合的模式映像 (使用编译的**/clr**)，结果映像将为混合的模式映像。  
  
 您可以使用 /CLRIMAGETYPE 根据需要指定较低级别的可验证性。  
  
 在 .NET 4.5 中，/CLRIMAGETYPE 支持 SAFE32BITPREFERRED 选项。 这将在映像的 PE 头中设置标志，指示 MSIL 对象是安全的，可以在所有平台上运行，但首选 32 位执行环境。 此选项使应用可以在 ARM 平台上运行，还指定它应在 64 位操作系统上的 WOW64 下运行，而不是使用 64 位执行环境。  
  
 时通过使用已编译的.exe **/clr**或**/clr: pure**运行在 64 位操作系统系统中，在允许 32 位应用程序在 64 位操作系统上运行的 WOW64 下运行应用程序。 默认情况下，通过使用编译的.exe **/clr: safe**操作系统的 64 位支持下运行。 但是，很可能你安全的应用程序加载 32 位组件。 在这种情况下，加载 32 位应用程序时，将失败安全映像操作系统的 64 位支持下运行。 若要确保安全映像在 64 位操作系统上加载 32 位组件时继续运行，请使用 /CLRIMAGETYPE:SAFE32BITPREFERRED 选项。 如果你的代码不必在 ARM 平台上运行，可以指定 /CLRIMAGETYPE:PURE 选项更改元数据 (.corflags)，使之在 WOW64 下运行（并替换为你自己的输入符号）：  
  
 **cl /clr:safe t.cpp /link /clrimagetype:pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 有关如何确定文件的 CLR 映像类型的信息，请参阅 [/CLRHEADER](../../build/reference/clrheader.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**高级**属性页。  
  
5.  修改**CLR 映像类型**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)