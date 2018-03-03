---
title: "-DYNAMICBASE （使用地址空间布局随机化） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1458070f85678d30c716622bf57740d90feb65d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE（使用地址空间布局随机化功能）
指定是否生成可执行映像可以是随机重新设定基址在加载时使用的地址空间布局随机化 (ASLR) 功能[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]。  
  
## <a name="syntax"></a>语法  
  
```  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，/DYNAMICBASE 处于打开。  
  
 此选项修改可执行文件以指示是否应用程序应随机重新设定基址在加载时的标头。  
  
 支持地址空间布局随机化[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**高级**属性页。  
  
5.  修改**随机基址**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)