---
title: "如何：在 Windows 桌面应用程序中使用 Windows 10 SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 如何：在 Windows 桌面应用程序中使用 Windows 10 SDK
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中创建经典 Windows 桌面项目时，默认设置为使用 Windows 8.1 SDK 进行生成。 此版本的 Windows SDK 与所有最新的 Windows 版本兼容，包括 Windows 10，但不包括 Windows 10 SDK 中最新的 Windows 10 API 和 CRT 函数。 如果要使用新 API，可重定向项目，以引用 Windows 10 SDK。  
  
 从 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 和 Windows 10 SDK 开始，CRT 库分为两个部分，一个部分 \(ucrtbase\) 包含通用 Windows 应用中接受使用的函数，另一部分 \(vcruntime140\) 包含所有其余内容。 由于 Windows 10 SDK 包含新函数（如许多 C99 函数），因此需要按照以下步骤进行操作以便使用这些函数。 请参阅 [CRT 库功能](../c-runtime-library/crt-library-features.md)。  
  
### 面向 Windows 10 SDK  
  
1.  确保已安装 Windows 10 SDK。 Windows 10 SDK 作为 [Windows 10 的工具](http://go.microsoft.com/fwlink/?LinkID=617631)的一部分进行安装。  
  
2.  打开项目节点的快捷菜单，然后选择**“重定向 SDK 版本”**。  
  
     ![重定 SDK 版本目标](../windows/media/retargetingwindowssdk1.png "RetargetingWindowsSDK1")  
  
     将显示**“查看解决方案操作”**对话框。  
  
     ![检查解决方案操作](../Image/RetargetingWindowsSDK2.PNG "RetargetingWindowsSDK2")  
  
3.  在**“目标平台版本”**下拉列表中，选择想要面向的 Windows 10 SDK 版本，如果不想进行任何更改，请选择 8.1。 选择“确定”按钮以应用更改。  
  
     请注意，此上下文中的 8.1 是指 Windows SDK 版本，它也向后兼容 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista。  
  
     如果此步骤成功，则输出窗口中将显示以下文本：  
  
     `重定向结束: 1 个已完成，0 个失败，0 个已跳过`  
  
4.  打开项目属性，然后在**“配置属性”\-\>“常规”**部分中查看**“Windows 目标平台版本”**的值。 更改此处的值与执行过程具有相同的效果。 请参阅 [“常规”属性页（项目）](../ide/general-property-page-project.md)。  
  
     ![目标平台版本](../windows/media/retargetingwindowssdk3.png "RetargetingWindowsSDK3")  
  
     此操作将更改项目宏的值，该项目宏中包含头文件和库文件的路径。 若要查看更改的内容，请在“项目属性”对话框的 Visual C\+\+ 目录部分中选择一个属性（如“包含目录”），然后选择打开下拉列表并选择编辑 \<编辑\>。 将显示**“包含目录”**对话框。  
  
     ![包含目录对话框](../windows/media/retargetingwindowssdk4.png "RetargetingWindowsSDK4")  
  
     选择**“宏 \>\>”**按钮，然后向下滚动宏列表到 Windows SDK 宏，以查看所有新值。  
  
     ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.png "RetargetingWindowsSDK5")  
  
5.  根据需要对其他项目重复以上步骤，并重新生成解决方案。  
  
### 面向 Windows 8.1 SDK  
  
1.  打开项目节点的快捷菜单，然后选择**“重定向 SDK 版本”**。  
  
2.  在“目标平台版本”下拉列表中，选择 8.1。  
  
## 请参阅  
 [Windows Desktop Applications \(Visual C\+\+\)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)