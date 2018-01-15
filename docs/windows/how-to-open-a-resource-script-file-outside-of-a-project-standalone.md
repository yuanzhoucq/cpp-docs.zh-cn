---
title: "如何： 打开项目 （独立） 外部的资源脚本文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resource
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2dd3bb3996fca1fd2c73ff98e7f391d27911ad15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>如何：在项目外打开资源脚本文件（独立）
你可以查看 .rc 文件中的资源，而不必打开项目。 .Rc 文件将在而不是在中打开的文档窗口中打开[资源视图](../windows/resource-view-window.md)窗口 （方式与其在项目内部打开文件时）。  
  
> [!NOTE]
>  这是一个重要的区别，因为仅当（在项目外部）独立打开该文件时才能显示某些命令。 例如，你可以仅保存文件以不同格式或不同的文件名称在项目外部打开文件时 (**另存为**如果在项目内部打开文件时，命令将不可用)。  
  
### <a name="to-open-an-rc-file-outside-a-project"></a>要在项目外部打开 .rc 文件  
  
1.  从**文件**菜单上，选择**打开**，然后单击**文件**。  
  
2.  在**打开的文件**对话框框中，导航到你想要查看，突出显示该文件，然后单击该资源脚本文件**打开**。  
  
    > [!NOTE]
    >  如果首先打开项目 (**文件**，**打开**，**项目**)，某些命令将不可用给您。 “单独”打开文件意味着不先加载项目而直接打开文件。  
  
 若要打开并以文本格式查看资源文件，请参阅[编辑资源脚本 (.rc) 文件](../windows/how-to-open-a-resource-script-file-in-text-format.md)。  
  
#### <a name="to-open-multiple-rc-files-outside-a-project"></a>若要在项目外部打开多个 .rc 文件  
  
1.  同时单独打开这两个资源文件。 例如，打开 Source1.rc 和 Source2.rc。  
  
    1.  从**文件**菜单上，选择**打开**，然后单击**文件**。  
  
    2.  在**打开文件**对话框框中，导航到你想要打开 (Source1.rc)，突出显示该文件，然后单击第一个资源脚本文件**打开**。  
  
    3.  重复上一步，打开第二个 .rc 文件 (Source2.rc)。  
  
         .Rc 文件即会在单独的文档窗口中打开。  
  
2.  当同时打开这两个 .rc 文件时，平铺窗口，以便可以同时查看它们：  
  
    -   从**窗口**菜单上，选择**新建水平制表符组**或**新建垂直制表符组**。  
  
         \- 或 -  
  
    -   右键单击其中一个.rc 文件，然后选择**新建水平制表符组**或**新建垂直制表符组**从快捷菜单。  
  
> [!NOTE]
>  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  

  
### <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)