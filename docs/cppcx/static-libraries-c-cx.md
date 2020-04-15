---
title: 静态库 (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358101"
---
# <a name="static-libraries-ccx"></a>静态库 (C++/CX)

通用 Windows 平台 （UWP） 应用中使用的静态库可以包含 ISO 标准C++代码（包括 STL 类型），还可以调用未从 Windows 运行时应用平台排除的 Win32 API。 静态库使用 Windows 运行时组件，并可能创建具有某些限制的 Windows 运行时组件。

## <a name="creating-static-libraries"></a>创建静态库

创建新项目的说明因已安装的 Visual Studio 版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建 UWP 静态库

1. 在菜单栏上，选择“文件”“新建”“项目”，打开“创建新项目”对话框**** > **** > ********。

1. 在对话框的顶部，将**语言**设置为**C++，** 将**平台**设置为**Windows，** 并将**项目类型**设置为**UWP**。

1. 从筛选的项目类型列表中，选择**静态库（通用 Windows - C++/CX），** 然后选择 **"下一步**"。 在下一页中，为项目指定名称，并根据需要指定项目位置。

1. 选择“创建”**** 按钮创建项目。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>在 Visual Studio 2017 或 Visual Studio 2015 中创建 UWP 静态库

1. 在菜单栏上，选择 **"文件** > **新项目** > **"。** 在**视觉C++** > **Windows 通用**选择**静态库（通用窗口）。**

1. 在**解决方案资源管理器**中，打开项目的快捷方式菜单，然后选择**属性**。 在"**属性"** 对话框中，在 **"配置属性** > **C/C++"** 页上，将 **"使用 Windows 运行时扩展**时间设置为**是"（/ZW）。**

::: moniker-end

编译新的静态库时，如果调用为 UWP 应用排除的 Win32 API，编译器将引发错误 C3861，"找不到标识符"。 要查找 Windows 运行时支持的替代方法，请参阅[UWP 应用中 Windows API 的替代方法](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

如果将静态库项目C++添加到 UWP 应用解决方案，则可能需要更新库项目的属性设置，以便 UWP 支持属性设置为 **"是**"。 如果没有此设置，代码将生成和链接，但在尝试验证 Microsoft 应用商店的应用时将发生错误。 编译静态库时的编译器设置应与使用该库的项目的编译器设置相同。

如果使用创建公共 `ref` 类、公共接口类或公共值类的静态库，则链接器会引发此警告：

> **警告 LNK4264：** 将使用 /ZW 编译的对象文件存档到静态库中;请注意，在创作 Windows 运行时类型时，不建议与包含 Windows 运行时元数据的静态库链接。

仅当静态库未生成在库本身之外使用的 Windows 运行时组件时，才能安全地忽略该警告。 如果该库不使用其定义的组件，则链接器可通过优化去除实现，即使公共元数据包含类型信息，情况也不例外。 这意味着，静态库中的公共组件将进行编译，但不会在运行时激活。 因此，任何 Windows 运行时组件（供其他组件或应用使用）都必须在动态链接库 （DLL） 中实现。

## <a name="see-also"></a>另请参阅

[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)
