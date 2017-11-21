---
title: "-SWAPRUN （链接器输出加载到交换文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs: C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f41a89e74ec2e9ed34e0add12717dd0c135ce723
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN（将链接器输出加载到交换文件）
```  
/SWAPRUN:{NET|CD}  
```  
  
## <a name="remarks"></a>备注  
 /SWAPRUN 选项通知链接器输出到一个交换文件，然后从那里运行映像的第一次复制到操作系统。 这是 Windows NT 4.0 （和更高版本） 功能。  
  
 如果指定 NET，则操作系统将首先将从网络的二进制映像复制到一个交换文件，并从那里加载它。 此选项可用于通过网络运行应用程序。 当指定 CD 时，操作系统将复制到一个页面文件的可移动磁盘上的映像，然后将其加载。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**系统**属性页。  
  
4.  修改以下属性之一：  
  
    -   **交换从 CD 运行**  
  
    -   **交换从网络运行**  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 属性。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)