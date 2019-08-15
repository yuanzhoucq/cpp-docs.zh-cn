---
title: 如何：在 Windows 桌面应用程序中使用 Windows 10 SDK
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513822"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：在 Windows 桌面应用程序中使用 Windows 10 SDK

在 Visual Studio 2017 中创建经典 Windows 桌面项目时, 默认情况下, 将设置该项目, 以使用安装或上次更新C++桌面工作负荷时安装的 WINDOWS 10 SDK 版本生成。 此版本的 Windows SDK 与 Windows 7 及更高版本兼容。 有关面向特定 Windows 版本的详细信息, 请参阅[使用 Windows 标头](/windows/win32/WinProg/using-the-windows-headers)。

如果要以早期版本的 SDK 为目标, 则可以打开 "**项目" |"属性**", 然后从 Windows SDK 版本 "下拉列表中可用的其他 SDK 版本中进行选择。

从 Visual Studio 2015 和 Windows 10 SDK 开始, CRT 库分为两个部分 (一个 (ucrtbase.dll)), 其中包含可在通用 Windows 应用中使用的函数, 另一个包含所有其他内容 (vcruntime140)。 由于 Windows 10 SDK 包含新函数（如许多 C99 函数），因此需要按照以下步骤进行操作以便使用这些函数。 请参阅 [CRT Library Features](../c-runtime-library/crt-library-features.md)。

### <a name="to-target-the-windows-10-sdk"></a>面向 Windows 10 SDK

1. 确保已安装 Windows 10 SDK。 Windows 10 SDK 作为**带有C++** 工作负荷的桌面开发的一部分进行安装。 适用于[Windows 10 的下载和工具](https://developer.microsoft.com/windows/downloads)中提供了独立版本。

2. 打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”** 。

   重![定目标 SDK 版本](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   将显示 **“查看解决方案操作”** 对话框。

   ![查看解决方案操作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. 在 "**目标平台版本**" 下拉列表中, 选择要作为目标的 WINDOWS 10 SDK 的版本。 选择“确定”按钮以应用更改。

   请注意，此上下文中的 8.1 是指 Windows SDK 版本，它也向后兼容 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista。

   如果此步骤成功，则输出窗口中将显示以下文本：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. 打开项目属性，然后在 **“配置属性”-&gt;“常规”** 部分中查看 **“Windows 目标平台版本”** 的值。 更改此处的值与执行过程具有相同的效果。 请参阅 [General Property Page (Project)](../build/reference/general-property-page-project.md)。

   ![目标平台版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   此操作将更改项目宏的值，该项目宏中包含头文件和库文件的路径。 若要查看所做的更改, 请在 "**项目属性**" 对话框的 "**可视C++目录**" 部分中, 选择其中一个属性 (如 "**包含目录**"), 选择\<打开下拉列表, 然后选择 "编辑 >"。 将显示 **“包含目录”** 对话框。

   !["包含目录" 对话框](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   选择 "**宏 >" >** "按钮, 然后向下滚动到 Windows SDK 宏的宏列表, 以查看所有新的值。

   ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. 根据需要对其他项目重复以上步骤，并重新生成解决方案。

### <a name="to-target-the-windows-81-sdk"></a>面向 Windows 8.1 SDK

1. 打开项目节点的快捷菜单，然后选择 **“重定向 SDK 版本”** 。

2. 在 "**目标平台版本**" 下拉列表中, 选择 " **8.1**"。

## <a name="see-also"></a>请参阅

[Windows 桌面应用程序 ( C++视觉对象)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)