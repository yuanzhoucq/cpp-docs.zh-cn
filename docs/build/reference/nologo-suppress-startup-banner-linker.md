---
title: "-NOLOGO （取消显示启动版权标志） （链接器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9cffaea51ad1ba17462292f4feae531361200d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO（取消显示启动版权标志）（链接器）
```  
/NOLOGO  
```  
  
## <a name="remarks"></a>备注  
 /NOLOGO 选项阻止显示版权消息和版本。  
  
 回显命令文件时，此选项还会取消取消。 有关详细信息，请参阅[LINK 命令文件](../../build/reference/link-command-files.md)。  
  
 默认情况下，此信息将发送到输出窗口链接器。 在命令行中，它将发送到标准输出，并可以定向到一个文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  此选项只应从命令行。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  此链接器选项不能以编程方式更改。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)