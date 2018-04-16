---
title: "/APPCONTAINER （UWP/Microsoft 应用商店应用） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc6e1d4c6e18cd2118571e57f671f85a0a3fb55
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER （Microsoft 应用商店应用）
指定链接器是否创建必须在应用程序容器中运行的可执行映像。  
  
## <a name="syntax"></a>语法  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，/APPCONTAINER 处于关闭状态。  
  
 此选项修改可执行文件以指示是否必须在 appcontainer 进程隔离环境中运行应用程序。 必须在 appcontainer 环境中运行应用指定 /APPCONTAINER — 例如，通用 Windows 平台 (UWP) 或 Windows Phone 8.x 应用程序。 （选项将自动设置 Visual Studio 中从模板创建的通用 Windows 应用时。）对于桌面应用，指定 /APPCONTAINER:NO 或只需忽略选项。  
  
 中引入了 /APPCONTAINER 选项[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**命令行**属性页。  
  
5.  在**其他选项**，输入`/APPCONTAINER`或`/APPCONTAINER:NO`。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)