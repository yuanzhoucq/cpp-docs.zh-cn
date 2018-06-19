---
title: 移植到通用 Windows 平台 (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2f94e54a8525d8d633374b3a23bafdfd93fee56
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846098"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>移植到通用 Windows 平台 (C++)
在本主题中，可以找到有关如何将现有的 C++ 代码移植到 Windows 10 应用平台（通用 Windows 平台）的信息。 术语 *“通用”* 的意思是代码可以在运行 Windows 10 的任何设备上运行，包括桌面、手机、平板电脑和运行 Windows 10 的未来设备。 可以创建单个项目和单个基于 XAML 的用户界面，可在运行 Windows 10 的任何设备上正常工作。 可以在 XAML 中使用动态布局功能，以允许应用的 UI 适应不同的显示大小。  
  
 Windows 开发人员中心文档包含将 Windows 8.1 应用移植到通用 Windows 平台的指南。 请参阅 [从 Windows Runtime 8 移动到 UWP](https://msdn.microsoft.com/windows/uwp/porting/w8x-to-uwp-root)。 尽管该指南主要侧重于 C# 代码，但指南的大部分内容都适用于 C++。 下面的过程包含更加详细的信息。  
  
 本主题包含以下用于将代码移植到 UWP 的过程。  
  
1.  [将 Windows 8.1 应用商店应用移植到 UWP](#BK_81StoreApp)  
  
2.  [将 Windows 8.1 运行时组件移植到 UWP](#BK_81Component)  
  
 如果具有经典的桌面 Win32 DLL，并且想要从 UWP 应用程序调用它，也可以执行此操作。 使用此类过程，可以为现有经典 Windows 桌面 C++ 应用程序或跨平台标准 C++ 代码创建 UWP 用户界面层。 请参阅[如何在通用 Windows 平台应用中使用现有 C++ 代码](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)。  
  
##  <a name="BK_81StoreApp"></a>将 Windows 8.1 应用商店应用移植到 UWP  
 如果拥有 Windows 8.1 应用商店应用，则可以使用此过程使其在 UWP 和运行 Windows 10 的任何设备上正常工作。  最好首先使用 Visual Studio 2017 将项目生成为 Windows 8.1 项目，以首先消除由编译器和库中的更改所引发的任何问题。 完成后，有两种方法可以将其转换为 Windows 10 UWP 项目。 最简单的方法（如下面的过程所述）是创建通用 Windows 项目，并将现有的代码复制到其中。 如果对 Windows 8.1 桌面和 Windows 8.1 手机使用通用项目，则你的项目开始时在 XAML 中有两个不同的布局，但最终只有一个调整至显示大小的动态布局。  
  
#### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>若要将 Windows 8.1 应用商店应用移植到 UWP  
  
1.  如果尚未完成此操作，则在 Visual Studio 2017 中打开 Windows 8.1 应用项目，并按照说明来升级项目文件。  
  
     需要在 Visual Studio 安装程序中安装 Windows 8.1 工具。 如果没有安装这些工具，请从“程序和功能”窗口启动 Visual Studio 安装程序，选择 Visual Studio 2017，并在安装程序窗口中选择“修改”。 找到 Windows 8.1 工具，确保其已选中，然后选择“确定”。  
  
2.  打开“项目属性”窗口，并在“C++”、“常规”下将平台工具集设置为 v141（适用于 Visual Studio 2017 的生成工具）。  
  
3.  将该项目生成为 Windows 8.1 项目，并解决任何生成错误。 在此阶段的任何错误可能是由于生成工具和库中的重大更改所引起的。 有关可能会影响代码的更改的详细说明，请参阅 [Visual C++ 更改历史记录（2003 - 2015）](../porting/visual-cpp-change-history-2003-2015.md)。  
  
     一旦项目已完全生成，则可以准备移植到通用 Windows (Windows 10) 中。  
  
4.  使用空白模板创建一个新的通用 Windows 应用项目。 你可能想要将其命名为与你现有的项目相同的名称，但是若要执行此操作，项目必须存在于不同的目录中。  
  
5.  关闭解决方案，然后使用 Windows 资源管理器或命令行，将 Windows 8.1 项目中的代码文件（具有扩展名 .cpp、.h 和 .xaml）复制到在步骤 1 中为该项目创建的项目文件 (.vcxproj) 所在的文件夹中。 请不要复制 Package.appxmanifest 文件，并且如果拥有 Windows 8.1 桌面和手机的单独代码，则选择其中一个代码首先进行移植（之后需要执行一些工作以适应另一个代码）。 请确保复制子文件夹及其内容。 如出现系统提示，请选择替换具有相同名称的所有文件。  
  
6.  重新打开该解决方案，并从项目节点的快捷菜单中选择 **“添加”、“现有项”** 。 选择所有复制的文件，任何已存在于项目中的文件除外。  
  
     检查所有子文件夹，并确保也在其中添加这些文件。  
  
7.  如果使用与旧项目不同的项目名称，则打开 Package.appxmanifest 文件并更新入口点，以反映应用类的命名空间名称。  
  
     Package.appxmanifest 文件中的 **“入口点”** 字段包含应用类的范围名称，其中包括包含应用类的命名空间。 当创建通用 Windows 项目时，命名空间设置为该项目的名称。 如果这不同于从旧项目中复制的文件的内容，则必须更新一个或另一个以使它们能够匹配。  
  
8.  生成项目并解决由不同版本的 Windows SDK 之间的重大更改所引发的任何生成错误。  
  
9. 在本地桌面上运行该项目。 验证不存在部署错误，并且应用的布局看起来合理，能在桌面上正常工作。  
  
10. 如果有单独的代码文件和 .xaml 用于其他设备（如 Windows Phone 8.1），则检查此代码并确定其与标准设备的差异。 如果其差异仅存在于布局中，则可能能够在 xaml 中使用“视觉状态管理器”根据屏幕大小自定义显示。 对于其他区别，可使用运用以下 #if 语句的代码中的条件部分。  
  
    ```  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
    ```  
  
     这些语句分别适用于 UWP 应用、Windows Phone 应用商店应用、都适用或都不适用（仅针对经典 Win32 桌面）。 这些宏仅在 Windows SDK 8.1 及更高版本中才可用，因此如果你的代码需要使用早期版本的 Windows SDK 或除 Windows 以外的其他平台进行编译，则还应考虑未定义它们中任何一个这种情况。  
  
11. 对应用支持的每种类型的设备，在仿真器或物理设备运行和调试应用。 若要运行仿真程序，则需在物理计算机上（而不是虚拟机上）运行 Visual Studio。  
  
##  <a name="BK_81Component"></a> 将 Windows 8.1 运行时组件移植到 UWP  
 如果有一个 DLL 或一个已使用 Windows 8.1 应用商店应用的 Windows 运行时组件，则可以使用此过程来获取使用 UWP 和 Windows 10 的组件或 DLL。 基本过程是创建新项目，然后将代码复制到其中。  
  
#### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>将 Windows 8.1 运行时组件移植到 UWP  
  
1.  在 Visual Studio 2017 的“新建项目”对话框中，找到“Windows 通用”节点。 如果看不到此节点，则首先安装 [用于 Windows 10 的工具](http://go.microsoft.com/fwlink/p/?LinkID=617903) 。 选择“Windows 运行时组件”  模板，给定组件名称，然后选择“确定”按钮  。 组件名称将被用作命名空间名称，因此你可能想要使用与旧项目的命名空间相同的名称。 这要求你在与旧文件夹不同的文件夹中创建该项目。 如果选择了一个不同的名称，则可以在生成的代码文件中更新命名空间名称。  
  
2.  关闭该项目。  
  
3.  将所有代码文件（.cpp、.h、.xaml 等）从 Windows 8.1 组件复制到新创建的项目中。 不要复制 Package.appxmanifest 文件。  
  
4.  生成，然后解决由不同版本的 Windows SDK 之间的重大更改所引发的任何错误。  
  
## <a name="troubleshooting"></a>疑难解答  
 在将代码移植到 UWP 的过程中，可能会遇到各种错误。 以下是一些可能遇到的问题。  
  
 **项目配置问题**  
  
 可能会收到以下错误：  
  
```Output  
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable  
```  
  
 如果发生这种情况，该项目不会生成为 Windows 通用项目。 检查项目文件，并确保其具有可将项目标识为 Windows 通用项目的正确的 XML 元素。 此时应该会存在以下元素（目标平台的版本号可能不同）：  
  
```xml  
<AppContainerApplication>true</AppContainerApplication>  
<ApplicationType>Windows Store</ApplicationType>  
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
```  
  
 如果使用 Visual Studio 创建新的 UWP 项目，则不应看到此错误。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 移植指南](../porting/porting-to-the-universal-windows-platform-cpp.md)   
 [开发通用 Windows 平台 (UWP) 的应用](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)
