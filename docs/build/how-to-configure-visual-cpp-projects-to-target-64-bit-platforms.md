---
title: 如何： 配置 Visual c + + 项目以面向 64 位 x64 平台
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: c0c734648b084c3f58577cb56984e3ea003a6a8e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523932"
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>如何： 配置 Visual c + + 项目以面向 64 位 x64 平台

可以使用 Visual Studio IDE 中的项目配置来设置 c + + 应用程序以面向 64 位 x64 平台。 还可以将 Win32 项目设置迁移到 64 位项目配置。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>设置项目以面向 64 位平台

1. 打开要配置的 C++ 项目。

1. 打开该项目的属性页面。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

   > [!NOTE]
   > 对于.NET 项目，请确保 **配置属性** 中选择节点或子节点之一**\<项目名称 > 属性页** 对话框; 否则为 **配置管理器**按钮仍然不可用。

1. 选择“配置管理器”  按钮以打开“配置管理器”  对话框。

1. 在中 **活动解决方案平台** 下拉列表中，选择 **\<新建...>** 选项来打开 **新建解决方案平台**对话框。

1. 在中**键入或选择新平台**下拉列表中，选择 64 位目标平台。

   > [!NOTE]
   > 在“新建解决方案平台”  对话框中，可以使用“从此处复制设置”  选项将现有项目设置复制到新的 64 位项目配置中。

1. 选择“确定”  按钮。 下面将显示你在上一步中选择的平台**活动解决方案平台**中**Configuration Manager**对话框。

1. 选择 **关闭** 按钮 **Configuration Manager** 对话框，然后再选择 **确定** 按钮在 **\<项目名称 >属性页** 对话框。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>将 Win32 项目设置复制到 64 位项目配置中

- 当设置面向 64 位平台的项目时，如果“新建解决方案平台”  对话框处于打开状态，请在“从此处复制设置”  下拉列表中选择“Win32” 。 在项目级别会自动更新这些项目设置：

  - [/MACHINE](../build/reference/machine-specify-target-platform.md) 链接器选项设置为 **/MACHINE:X64**。

  - 关闭“注册输出” 。 有关详细信息，请参阅 [Linker Property Pages](../ide/linker-property-pages.md)。

  - “目标环境” 设置为 **/env x64**。 有关详细信息，请参阅 [MIDL Property Pages: General](../ide/midl-property-pages-general.md)。

  - “验证参数” 被清除并且重置为默认值。 有关详细信息，请参阅 [MIDL Property Pages: Advanced](../ide/midl-property-pages-advanced.md)。

  - 如果在 Win32 项目配置中已将“调试信息格式”  设置为 **/ZI** ，则在 64 位项目配置中将设置为 **/Zi** 。 有关详细信息，请参阅 [/Z7、/Zi、/ZI（调试信息格式）](../build/reference/z7-zi-zi-debug-information-format.md)。

  > [!NOTE]
  > 如果在文件级重写，则不会更改这些项目属性。

## <a name="see-also"></a>请参阅

[.NET framework 64 位应用程序](/dotnet/framework/64-bit-apps)<br/>
[针对 64 位 x64 目标配置 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[调试 64 位应用程序](/visualstudio/debugger/debug-64-bit-applications)