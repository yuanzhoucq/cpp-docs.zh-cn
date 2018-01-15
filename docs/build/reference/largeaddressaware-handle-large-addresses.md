---
title: "-LARGEADDRESSAWARE （处理大地址） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs: C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ecda14f6faf7230066bb1c2b374ca475cc98cb1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE（处理大地址）
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>备注  
 /LARGEADDRESSAWARE 选项通知链接应用程序能够处理大于 2 千兆字节的地址。 在 64 位编译器中，默认情况下启用此选项。 在 32 位编译器中，如果 /LARGEADDRESSAWARE 否则未指定链接器行上启用 /LARGEADDRESSAWARE:NO。  
  
 如果应用程序已链接使用 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)将显示针对此效果的信息。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**系统**属性页。  
  
4.  修改**启用大地址**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)