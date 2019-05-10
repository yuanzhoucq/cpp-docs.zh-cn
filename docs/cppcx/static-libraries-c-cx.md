---
title: 静态库 (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 188ba06518bf6cdd154b7d6bd61216ed1e4ffad3
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877247"
---
# <a name="static-libraries-ccx"></a>静态库 (C++/CX)

在通用 Windows 平台 (UWP) 应用中使用的静态库可以包含 ISO 标准C++代码，包括 STL 类型，同时还不从 Windows 运行时应用平台中排除的 Win32 Api 调用。 静态库使用 Windows 运行时组件，并可能会创建 Windows 运行时组件具有某些限制。

## <a name="creating-static-libraries"></a>创建静态库


说明如何创建一个新的项目已安装 Visual Studio 的版本而异。 请确保你拥有版本选择器右上角设置为正确的版本。

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中创建 UWP 静态库

1. 在菜单栏上依次选择**文件** > **新建** > **项目**打开**创建一个新项目**对话框。

1. 在对话框顶部，设置**语言**到**C++**，将**平台**到**Windows**，并设置**项目类型**到**UWP**。 

1. 从已筛选的项目类型列表中，选择**静态库 (通用 Windows- C++/CX)** 然后选择**下一步**。 在下一步的页中，为项目提供一个名称，并根据需要指定项目位置。

1. 选择**创建**按钮创建项目。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>若要在 Visual Studio 2017 或 Visual Studio 2015 中创建 UWP 静态库

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。 下**可视化C++**   >  **Windows Universal**选择**静态库 (通用 Windows)**。

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。 在中**属性**对话框中，在**配置属性** > **C /C++** 页上，设置**使用 Windows 运行时扩展**到**是 (/ZW)**。

::: moniker-end

当你编译新的静态库，如果一个适用于 UWP 应用中排除的 Win32 API 调用时，编译器将引发错误 C3861"找不到标识符"。 若要查找的 Windows 运行时支持一种替代方法，请参阅[UWP 应用中的 Windows Api 的替代方法](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

如果添加C++静态库项目到 UWP 应用解决方案中，您可能必须更新该库项目的属性设置，使 UWP 支持属性设置为**是**。 如果没有此设置，代码将生成，当尝试验证的 Microsoft Store 应用的链接，但出现错误时发生。 编译静态库时的编译器设置应与使用该库的项目的编译器设置相同。

如果使用创建公共 `ref` 类、公共接口类或公共值类的静态库，则链接器会引发此警告：

> **warning LNK4264:** 归档到静态库中; 使用 /ZW 编译的对象文件请注意，创作 Windows 运行时类型时不建议以包含 Windows 运行时元数据的静态库链接。

仅当静态库不生成在库自身之外被使用的 Windows 运行时组件，可以放心地忽略该警告。 如果该库不使用其定义的组件，则链接器可通过优化去除实现，即使公共元数据包含类型信息，情况也不例外。 这意味着，静态库中的公共组件将进行编译，但不会在运行时激活。 出于此原因，必须在动态链接库 (DLL) 中实现由其他组件或应用程序旨在用于使用任何 Windows 运行时组件。

## <a name="see-also"></a>请参阅

[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)
