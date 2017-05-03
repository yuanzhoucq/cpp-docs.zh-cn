---
title: "DLL (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 21
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 21
---
# DLL (C++/CX)
可以使用 Visual Studio 创建可以由 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]应用程序使用的标准 Win32 DLL 或 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]组件 DLL。 使用 [!INCLUDE[vs_dev11_long](../cppcx/includes/vs-dev11-long-md.md)] 之前的 Visual Studio 或 Visual C\+\+ 编译器版本创建的标准 DLL 可能无法在 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序中正确加载，并且可能无法通过 [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]中的应用程序验证测试。  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件 DLL  
 在几乎任何情况下，当你要创建在 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序中使用的 DLL 时，可使用该名称的项目模板将其创建为 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件。 你可以为具有公共或私有 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型的 DLL 创建一个 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件项目。 可以从用任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]兼容语言编写的应用程序访问 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件。 默认情况下，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件项目的编译器设置使用 **\/ZW** 开关。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。  
  
 有关详细信息，请参阅[用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)。  
  
#### 在项目中引用第三方 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件二进制文件  
  
1.  打开将要使用该 DLL 的项目的快捷菜单，然后选择**“属性”**。 在**“公共属性”**页上，选择**“添加新引用”**按钮。  
  
2.  [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件由 DLL 文件和包含元数据的 .winmd 文件组成。 通常，这些文件位于同一文件夹中。 在**“添加引用”**对话框的左窗格中，选择**“浏览”**按钮，然后定位到该 DLL 及其 .winmd 文件的位置。 有关更多信息，请参见[教程：创建和使用扩展 SDK](http://msdn.microsoft.com/zh-cn/001e2fca-3d56-43ab-a5e0-0561d085679f)。  
  
## 标准 DLL  
 可以为不使用或者不产生公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型的 C\+\+ 代码创建标准 DLL，并从 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用中使用它。 当您只希望迁移要在该版本的 Visual Studio 中编译的现有 DLL 而不是将代码转换为 Windows 运行时组件项目时，请使用 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL 项目类型。 在使用下列步骤时，将在 .appx 包中的应用程序可执行文件旁边部署 DLL。  
  
#### 在 Visual Studio 中创建标准 DLL  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**和“[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL”模板。  
  
2.  输入项目名称，然后选择**“确定”**按钮。  
  
3.  添加代码。 确保将 `__declspec(dllexport)` 用于你准备导出的函数，例如 `__declspec(dllexport) Add(int I, in j);`  
  
4.  添加 `#include winapifamily.h` 以包括来自 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序的 Windows SDK 的该标头文件，并设置宏 `WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
#### 从同一解决方案引用标准 DLL 项目  
  
1.  打开将要使用该 DLL 的项目的快捷菜单，然后选择**“属性”**。 在**“公共属性”**页上，选择**“添加新引用”**按钮。  
  
2.  在左窗格中，选择**“解决方案”**，然后在右窗格中选中相应的复选框。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  
#### 引用标准 DLL 二进制文件  
  
1.  复制 DLL 文件、.lib 文件和标头文件，将它们粘贴到一个已知位置（如你的当前项目文件夹中）。  
  
2.  打开将要使用该 DLL 的项目的快捷菜单，然后选择**“属性”**。 在**“配置属性”**\>**“链接器”**\>**“输入”**页上，添加 .lib 文件作为依赖项。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  
#### 迁移现有 Win32 DLL 以实现 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序兼容性  
  
1.  创建 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL 类型的项目，然后向其中添加你现有的源代码。  
  
2.  添加 `#include winapifamily.h` 以包括来自 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序的 Windows SDK 的该标头文件，并设置宏 `WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  
## 请参阅  
 [\(NOTINBUILD\) 高级主题](http://msdn.microsoft.com/zh-cn/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)