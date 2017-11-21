---
title: "-FUNCTIONPADMIN （创建可热修补的映像） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /functionpadmin
dev_langs: C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f286cf0cb595f640768f97c1619517f6000fd39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN（创建可热修补的映像）
准备要热修补的映像。  
  
## <a name="syntax"></a>语法  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `space`（可选）  
 要将添加到每个函数的开头的填充量 5、 6 或 16。  x86 映像需要的填充，x64 映像需要 6 个字节和构建的 Itanium 处理器家族映像需要的每个函数的开头填充 16 个字节的五个字节。  
  
 默认情况下，编译器将添加到映像，基于映像的计算机类型的正确的空间量。  
  
 为了使链接器以生成可热修补图像，.obj 文件都必须已使用编译[/hotpatch （创建可热修补的映像）](../../build/reference/hotpatch-create-hotpatchable-image.md)。  
  
 在编译和链接单次调用 cl.exe，与映像**/hotpatch**意味着**/functionpadmin**。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  该选项键入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)