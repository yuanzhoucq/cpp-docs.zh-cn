---
title: -WINMDKEYFILE (指定 winmd 密钥文件) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba19ddd7a9ca1c313cc9f72e6cc8b77b4b565ceb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE（指定 winmd 密钥文件）
指定用来登录 Windows 运行时元数据 (.winmd) 文件的密钥或密钥对。  
  
```  
/WINMDKEYFILE:filename  
```  
  
## <a name="remarks"></a>备注  
 类似于[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)应用于.winmd 文件的链接器选项。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**Windows 元数据**属性页。  
  
4.  在**Windows 元数据密钥文件**框中，输入文件位置。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)