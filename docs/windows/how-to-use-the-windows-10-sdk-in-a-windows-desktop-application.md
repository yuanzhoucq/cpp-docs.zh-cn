---
title: "如何： 使用 Windows 10 SDK 中的 Windows 桌面应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f5e6f09b371c4d295b4bcdff469396a2671d22a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：在 Windows 桌面应用程序中使用 Windows 10 SDK
当你在 Visual Studio 2017 年 1 中创建经典 Windows 桌面项目时，它是默认设置使用 c + + 桌面工作负荷的安装或上次更新一起安装的 Windows 10 sdk 的版本进行生成。 此版本的 Windows SDK 是与所有最新的 Windows 版本兼容。 如果你想要面向的 sdk 的早期版本，则可以打开项目 |属性，然后选择从其他 Windows SDK 版本下拉列表中提供的 SDK 版本。  
  
 从 Visual Studio 2015 和 Windows 10 SDK 开始，CRT 库分为两个部分，一个部分 (ucrtbase) 包含可接受要在通用 Windows 应用程序中使用的函数 (vcruntime140) 包含所有的一个。 由于 Windows 10 SDK 包含新函数（如许多 C99 函数），因此需要按照以下步骤进行操作以便使用这些函数。 请参阅 [CRT 库的功能](../c-runtime-library/crt-library-features.md)。  
  
### <a name="to-target-the-windows-10-sdk"></a>面向 Windows 10 SDK  
  
1.  确保已安装 Windows 10 SDK。 作为的一部分安装 Windows 10 SDK[工具适用于 Windows 10](http://go.microsoft.com/fwlink/p/?linkid=617631)。  
  
2.  打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”**。  
  
     ![重定向 SDK 版本](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     将显示 **“查看解决方案操作”** 对话框。  
  
     ![查看解决方案操作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  在**目标平台版本**下拉列表中，选择想要面向的 Windows 10 sdk 版本。 选择“确定”按钮以应用更改。  
  
     请注意，此上下文中的 8.1 是指 Windows SDK 版本，它也向后兼容 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista。  
  
     如果此步骤成功，则输出窗口中将显示以下文本：  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  打开项目属性，然后在 **“配置属性”-&gt;“常规”** 部分中查看 **“Windows 目标平台版本”**的值。 更改此处的值与执行过程具有相同的效果。 请参阅 [General Property Page (Project)](../ide/general-property-page-project.md)。  
  
     ![指定的目标平台版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     此操作将更改项目宏的值，该项目宏中包含头文件和库文件的路径。 若要查看更改的内容，项目属性对话框中，Visual c + + 目录部分中选择一个属性，例如包含目录，选择打开下拉列表中，然后选择\<编辑 >。 将显示 **“包含目录”** 对话框。  
  
     ![包含目录对话框](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     选择**宏 >>**按钮，然后向下滚动到 Windows SDK 宏，以查看所有新值的宏的列表。  
  
     ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  根据需要对其他项目重复以上步骤，并重新生成解决方案。  
  
### <a name="to-target-the-windows-81-sdk"></a>面向 Windows 8.1 SDK  
  
1.  打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”**。  
  
2.  在“目标平台版本”下拉列表中，选择 8.1。  
  
## <a name="see-also"></a>请参阅  
 [Windows 桌面应用程序 （Visual c + +）](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
