---
title: -WINMDDELAYSIGN （部分 winmd 的登录） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c50480fae1f4f3e7421236615d059a642d1074f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN（对 winmd 进行部分签名）
通过将公钥部分放在 Windows 运行时元数据 (.winmd) 文件中来启用该文件的部分签名。  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>备注  
 类似于[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)应用于.winmd 文件的链接器选项。 使用 **/WINMDDELAYSIGN**如果你想要将仅将公钥放在.winmd 文件。 默认情况下，链接器的作用如同 **/WINMDDELAYSIGN:NO**指定; 也就是说，它不会不签名 winmd 文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**Windows 元数据**属性页。  
  
4.  在**Windows 元数据延迟签名**下拉列表框中，选择所需的选项。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)