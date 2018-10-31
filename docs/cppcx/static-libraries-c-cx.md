---
title: 静态库 (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 4c423f9e59b7597782acfa4c98db3c9bff747098
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437943"
---
# <a name="static-libraries-ccx"></a>静态库 (C++/CX)

在通用 Windows 平台 (UWP) 应用中使用的静态库可以包含 ISO 标准 c + + 代码，包括 STL 类型，同时还不从 Windows 运行时应用平台中排除的 Win32 Api 调用。 静态库使用 Windows 运行时组件，并可能会创建 Windows 运行时组件具有某些限制。

## <a name="creating-static-libraries"></a>创建静态库

#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>若要创建 UWP 应用中使用的静态库

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。 下**Visual c + +** > **Windows Universal**选择**静态库 (通用 Windows)**。

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。 在中**属性**对话框中，在**配置属性** > **C/c + +** 页上，设置**使用Windows运行时扩展**到**是 (/ZW)**。

当你编译新的静态库，如果一个适用于 UWP 应用中排除的 Win32 API 调用时，编译器将引发错误 C3861"找不到标识符"。 若要查找的 Windows 运行时支持一种替代方法，请参阅[UWP 应用中的 Windows Api 的替代方法](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

如果将 c + + 静态库项目添加到 UWP 应用程序解决方案，您可能必须更新该库项目的属性设置，使 UWP 支持属性设置为**是**。 如果没有此设置，代码将生成，当尝试验证的 Microsoft Store 应用的链接，但出现错误时发生。 编译静态库时的编译器设置应与使用该库的项目的编译器设置相同。

如果使用创建公共 `ref` 类、公共接口类或公共值类的静态库，则链接器会引发此警告：

> **warning LNK4264:** 归档到静态库中; 使用 /ZW 编译的对象文件请注意，创作 Windows 运行时类型时不建议以包含 Windows 运行时元数据的静态库链接。

仅当静态库不生成在库自身之外被使用的 Windows 运行时组件，可以放心地忽略该警告。 如果该库不使用其定义的组件，则链接器可通过优化去除实现，即使公共元数据包含类型信息，情况也不例外。 这意味着，静态库中的公共组件将进行编译，但不会在运行时激活。 出于此原因，必须在动态链接库 (DLL) 中实现由其他组件或应用程序旨在用于使用任何 Windows 运行时组件。

## <a name="see-also"></a>请参阅

[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)