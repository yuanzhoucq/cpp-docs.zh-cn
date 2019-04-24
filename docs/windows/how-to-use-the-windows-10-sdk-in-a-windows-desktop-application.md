---
title: 如何：使用 Windows 10 SDK 中的 Windows 桌面应用程序
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: f3f6897dfa0f180f629a2ca169ff74c5e5588365
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021523"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：使用 Windows 10 SDK 中的 Windows 桌面应用程序

当在 Visual Studio 2017 中创建经典 Windows 桌面项目时，它默认设置使用的是 Windows 10 SDK 版本进行生成时安装C++桌面工作负载的安装或上一次更新。 Windows 7 和更高版本，此版本的 Windows SDK 都兼容。 请参阅[使用 Windows 标头](/windows/desktop/WinProg/using-the-windows-headers)有关面向特定版本 Windows 的详细信息。

如果你想要面向早期版本的 sdk，则可以打开**项目 |属性**，然后选择从 Windows SDK 版本下拉列表中提供的其他 SDK 版本。

从 Visual Studio 2015 和 Windows 10 SDK 开始，CRT 库分为两个部分，一个 (ucrtbase) 包含可接受要在通用 Windows 应用程序中使用的函数，其他所有内容 (vcruntime140) 包含的一个。 由于 Windows 10 SDK 包含新函数（如许多 C99 函数），因此需要按照以下步骤进行操作以便使用这些函数。 请参阅 [CRT Library Features](../c-runtime-library/crt-library-features.md)。

### <a name="to-target-the-windows-10-sdk"></a>面向 Windows 10 SDK

1. 确保已安装 Windows 10 SDK。 Windows 10 SDK 安装的一部分**使用的桌面开发C++** 工作负荷。 独立版是在[下载和工具适用于 Windows 10](https://developer.microsoft.com/windows/downloads)。

2. 打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”**。

   ![重定向 SDK 版本](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   将显示 **“查看解决方案操作”** 对话框。

   ![查看解决方案操作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. 在中**目标平台版本**下拉列表中，选择想要面向的 Windows 10 sdk 版本。 选择“确定”按钮以应用更改。

   请注意，此上下文中的 8.1 是指 Windows SDK 版本，它也向后兼容 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista。

   如果此步骤成功，则输出窗口中将显示以下文本：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. 打开项目属性，然后在 **“配置属性”-&gt;“常规”** 部分中查看 **“Windows 目标平台版本”** 的值。 更改此处的值与执行过程具有相同的效果。 请参阅 [General Property Page (Project)](../build/reference/general-property-page-project.md)。

   ![目标平台版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   此操作将更改项目宏的值，该项目宏中包含头文件和库文件的路径。 若要查看更改的内容，在**可视化C++目录**一部分**项目属性**对话框中，选择其中一个属性，例如**包含目录**，选择打开下拉列表中，并选择\<编辑 >。 将显示 **“包含目录”** 对话框。

   ![包含目录对话框](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   选择**宏 >>** 按钮，然后向下滚动以查看所有新值的 Windows SDK 宏的宏的列表。

   ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. 根据需要对其他项目重复以上步骤，并重新生成解决方案。

### <a name="to-target-the-windows-81-sdk"></a>面向 Windows 8.1 SDK

1. 打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”**。

2. 在中**目标平台版本**下拉列表中，选择**8.1**。

## <a name="see-also"></a>请参阅

[Windows 桌面应用程序 (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)