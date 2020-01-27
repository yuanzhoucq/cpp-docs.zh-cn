---
title: 如何：在 Windows 桌面应用程序中使用 Windows 10 SDK
description: 如何在 Windows 桌面应用程序项目中将目标 SDK 版本设置为使用 Windows 10 SDK。
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725729"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：在 Windows 桌面应用程序中使用 Windows 10 SDK

在 Visual Studio 中创建新的经典 Windows 桌面项目时，默认情况下它以 Windows 10 SDK 为目标。 安装C++桌面工作负载时，Visual Studio 会安装此 SDK 的版本。 Windows 10 SDK 支持编写适用于 Windows 7 SP1 及更高版本的代码。 有关面向特定 Windows 版本的详细信息，请参阅[使用 Windows 标头](/windows/win32/WinProg/using-the-windows-headers)并[更新 WINVER 和 _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md)。

升级现有项目时，可以选择：使用项目中指定的目标 Windows SDK。 或者，你可以将项目重定目标为使用 Windows 10 SDK。 通过 Windows 10 SDK，你可以获得对最新操作系统和语言标准的支持。

## <a name="use-the-right-windows-sdk-for-your-project"></a>为项目使用正确的 Windows SDK

从 Visual Studio 2015 开始，C 运行时（CRT）库分为两部分：一个部分 ucrtbase.dll，其中包含可在通用 Windows 应用中使用的标准 C 和 Microsoft 特定 CRT 函数。 此库现在称为通用 CRT 或 UCRT，已移动到 Windows 10 SDK。 UCRT 包含许多新功能，如支持最新C++语言标准所需的 C99 函数。 原始 CRT 的其他部分为 vcruntime。 它包含 C 运行时支持、启动和终止代码，以及未进入 UCRT 的所有其他内容。 Vcruntime 库与 Visual Studio 中的C++编译器和工具集一起安装。 有关详细信息，请参阅[CRT 库功能](../c-runtime-library/crt-library-features.md)。

现在，UCRT 是安装在 Windows 10 的每个版本上的系统组件。 它还可作为所有早期支持的 Windows 版本的可安装组件。 您可以使用 Windows 10 SDK 来面向所有受支持的 Windows 版本。 有关支持的操作系统的完整列表，请参阅[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

若要在从 Visual Studio 2015 之前的项目版本升级时将项目重定目标为使用 Windows 10 SDK，请执行以下步骤：

### <a name="to-target-the-windows-10-sdk"></a>面向 Windows 10 SDK

1. 确保已安装 Windows 10 SDK。 Windows 10 SDK 作为**带有C++** 工作负荷的桌面开发的一部分进行安装。 适用于[Windows 10 的下载和工具](https://developer.microsoft.com/windows/downloads)中提供了独立版本。

1. 打开项目节点的快捷菜单，然后选择 "重**定目标项目**"。 （在早期版本的 Visual Studio 中，选择 "重**定目标 SDK 版本**"。）此时将显示 "**查看解决方案操作**" 对话框。

   ![查看解决方案操作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. 在 "**目标平台版本**" 下拉列表中，选择要作为目标的 WINDOWS 10 SDK 的版本。 一般来说，建议选择最新安装的版本。 选择 "**确定"** 按钮以应用更改。

   此上下文中的8.1 是指 Windows 8.1 SDK。

   如果此步骤成功，则输出窗口中将显示以下文本：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. 打开 "项目属性" 对话框。 在 "**配置属性** > "**常规**"部分中，注意**Windows" 目标平台版本**"的值。 更改此处的值与执行过程具有相同的效果。 有关详细信息，请参阅[“常规”属性页（项目）](../build/reference/general-property-page-project.md)。

   ![目标平台版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   此操作将更改项目宏的值，该项目宏中包含头文件和库文件的路径。 若要查看更改的内容，请打开 "**项目属性**" 对话框的 "**可视C++目录**" 部分。 选择其中一个属性，如 "**包含目录**"。 然后，打开属性值的下拉列表，然后选择 " **\<编辑 >** "。 将显示 **“包含目录”** 对话框。

   !["包含目录" 对话框](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   选择 "**宏 >" >** "按钮，然后向下滚动到 Windows SDK 宏的宏列表，以查看所有新的值。

   ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. 根据需要对其他解决方案项目重复执行重定目标过程，并重新生成解决方案。

### <a name="to-target-the-windows-81-sdk"></a>面向 Windows 8.1 SDK

1. 在解决方案资源管理器中打开项目节点的快捷菜单，然后选择 "重**定目标项目**"。 （在早期版本的 Visual Studio 中，选择 "重**定目标 SDK 版本**"。）

2. 在 "**目标平台版本**" 下拉列表中，选择 " **8.1**"。

## <a name="see-also"></a>另请参阅

[演练：创建传统的 Windows 桌面应用程序C++（）](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
